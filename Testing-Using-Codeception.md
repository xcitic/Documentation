## Functional Tests 
Functional tests don't require a web server. 

They are usually much faster than acceptance tests (end to end), however functional tests are less stable as they run Codeception and
the application in one environment. 

Functional tests will get some header errors because it runs the application multiple times, this is to be expected.

You can use Guzzle to open external URLS. 

Functional tests run with shared memory, so they might pollute each others memory space. 
Keep in mind that if your using globals then each test should be run independently, because they might change the global variables. 

### Setting up functional tests for Symfony
+ functional.suite.yml
```
actor: FunctionalTester
modules:
    enabled:
        - Symfony
        - Doctrine2:
            depends: Symfony # connect to Symfony
```

### Writing Functional Tests 
Functional tests are written in the same manner as Acceptance Tests with the PHPbrowser module enabled. 
Share the same methods and the same engine. 
--> To open up a page <br/>
$I->amOnPage('/login');



## Unit & Integration Tests 
Uses PHPUnit as backend for running tests. PHPUnit tests can be added to Codeception test suite and then executed. 
Codeception adds some helpers to simplify common tasks. 

+ Creating a test <br/>
` codecept g:test unit UserTest `

All public methods with test prefix are tests and get run.
_before method is executed before each test. (setUp in PHPUnit) 
_after method is executed after each test.  (tearDown in PHPUnit)

Here is an example of a unit test to test the validation of username.
```php
class UserTest extends \Codeception\Test\Unit
{
    public function testUsernameValidation()
    {
        $user = new User();
        
        $user->setName(null);
        $user->assertFalse($user->validate(['username']);
        
        $user->setName('tooooooolooooongname');
        $user->assertFalse($user->validate(['username']);
        
        $user->setName('Sami');
        $user->assertTrue($user->validate(['username']);
    }
}
```

Most common used assertions are:
```php
    $this->assertEquals()
    $this->assertContains()
    $this->assertFalse()
    $this->assertTrue()
    $this->assertNull()
    $this->assertEmpty()
 ```

For mocking data Codeception provides Codeception\Stub library. It uses PHPUnits mock builder under the hood, but exposes a simpler API.
Alternatively Mockery can be used inside Codeception. 

### Stubs
```php
// create a stub with find method replaced 
$userRepo = $this->make(UserRepository::class, ['find' => new User]);
$userRepo->find(1); // => User 

// create a dummy 
$userRpo = $this->makeEmpty(UserRepo::class);

// create a stub with all methods replaced except one
$user = $this->makeEmptyExcept(User::class, 'validate');
$user->validate($data);

// create a stub by calling constructor and replacing a method
$user = $this->construct(User::class, ['name' => 'davert'], ['save' => false]);

// create a stub by calling constructor with empty methods
$user = $this->constructEmpty(User::class, ['name' => 'davert']);

// create a stub by calling constructor with empty methods
$user = $this->constructEmptyExcept(User::class, 'getName', ['name' => 'davert']);
$user->getName(); // => davert
$user->setName('jane'); // => this method is empty
```


### Mocks 
```php
// create a mock where $user->getName() should never be called
$user = $this->make('User', [
     'getName' => Expected::never(),
     'someMethod' => function() {}
]);
$user->someMethod();

// create a mock where $user->getName() should be called at least once
$user = $this->make('User', [
        'getName' => Expected::atLeastOnce('Davert')
    ]
);
$user->getName();
$userName = $user->getName();
$this->assertEquals('Davert', $userName);
```

## Integration Tests 
Integration tests combine multiple unit tests and allow us to use database and other components inside a test. 
This is made possible through Modules, and if you write integration tests it would be useful to include the 
Db module. 

### Including Modules 
```yaml  
# Codeception Test Suit Config 
# Suite for unit tests 
actor: UnitTester
modules:
    enabled:
       - Asserts
       - Db
       - \Helper\Unit 
``` 

### Testing Database 
To enable db functionality in unit test, make sure the Db module is included in the unit.suite.yml configuration file. 
The database will be cleaned and populated after each test, the same way it happens for acceptance and functional tests. 
If that is not the required behavior, change the settings of the Db module for the current suite. Check out <a href="https://codeception.com/docs/modules/Db">DB module</a>

```php
function testSavingUser() 
{
    $user = new User();
    $user->setName('Sami');
    $user->setSurname('Lazreg');
    $user->save();
    $user->assertEquals('Sami Lazreg', $user->getFullName());
    $user->tester->seeInDatabase('users', ['name' => 'Sami', 'surname' => 'Lazreg']);
}
```

### Testing the database using the frameworks ORM 
Codeception allows interacting through the ORM system of your framework. For symfony that is Doctrine, while for Laravel the ORM is Eloquent. 
To enable this you have to add the module in the config. 
```yaml
actor: UnitTester
modules:
    enabled:
        - Asserts
        - Doctrine2:
            depends: Symfony
        - \Helper\Unit
```


