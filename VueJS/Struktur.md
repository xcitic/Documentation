## Ressurser som er nyttige

[VueJS Main Documentation](https://vuejs.org/)

[VueJS Essential Cheat sheet](https://www.vuemastery.com/pdf/Vue-Essentials-Cheat-Sheet.pdf)

[VueJS LifeCycle Hooks](https://alligator.io/vuejs/component-lifecycle/)

[Vuex Store | State Management](https://vuex.vuejs.org/)

[VueRouter | Single Page Application](https://router.vuejs.org/)

[NativeScript | Cross-Platform VueJS](https://www.nativescript.org/)


## Verktøy som bør installeres 
+ Vue CLI 
+ NodeJS
+ Yarn (husk å nevne at man enten bruker Yarn eller NPM !!NB IKKE BEGGE DELER I SAMME PROSJEKT)
+ Vue DevTools


## Hva trenger man å kunne for å bruke VueJS? 
+ Forstå hva VueJS er

+ Forstå hvordan man inkluderer VueJS i en applikasjon

+ Mounte en komponent til en html div

+ Forstå strukturen og oppsett av en .vue file 

+ Ha et overblikk over de ulike API metodene som er tilgjenglige i Vue

+ Data property 
    + Forstå hva data properties er 
    + Forstå hvordan man lager data properties 
 

+ Forstå hvordan man bruker data med `{{ data }}`

+ Forstå hvordan man bruker Expressions
    + Ternary operator `{{ vue ? 'is easy' : 'practise makes master' }}`
    + Function `{{ vue.test() }}`
    + Concatenation `{{ vue + 'is easy' }}`

+ Forstå hvordan man bruker `v-bind`
    + Short form `:`
    + Legge til en css klasse avhenging av en data property
    + Disable knapper med `:disabled="submitted"`
    + Binde image src 
    + Binde achor tags href 
    + Binde style som data property

+ Forstå hvordan man bruker `v-on`
    + Short form `@`
    + Kalle funksjoner ved klikk
    + Sende argumenter med funksjon kall 
    + Unngå page reload med .preventDefault || .prevent 
    + Forstå keyboard modifers sin plass, og forstå default behavior modifers sin plass
    + Andre keyboard modifiers (TODO link her)
    + Andre default behavior modifers (TODO link her)
    
+ Forstå Directives 
    + If elseif else statements `v-if v-else-if v-else` 
    + Bruke en if statement til å mounte en komponent avhengig av data property
    + Bruke en if statement til å vise en tekst hvis man er logget in 
        + Bruke en else statement til å vise login knapp hvis man ikke er logget inn 

    + Kunne bruke `v-show`
        + Når kan man bruke `v-show`
    
    
+ Forstå hvordan man binder two-way reactive data med `v-model`
    + Forstå bruken av `v-model.lazy`
    + Forstå bruken av `v-model.number`
    + Forstå bruken av `v-model.trim`

+ List rendering     
    + Hvordan man binder foreach loop `v-for`
    + Hvorfor man skal ha med en index key `v-for="(item, index) in items" :key="index"`
    + Alternative måter å gi unik key `v-for="item in items" :key="item.id"`
    + Iterer over objekter i en associative array `v-for="(value, key) in object" :key="key"`

+ Props 
    + Hvorfor man trenger å "sende" props nedover i komponenter 
    + Hvordan man sender props 
    + Mounting av props til data properties in komponenten
    + Unngå duplikat av data og props 
    + Alternativer til å sende props === Vuex Store
    
+ Events 
    + Hvorfor man trenger å "emitte" eventer oppover i komponenter til en "listener" observer
    + Sette opp en "listener" på parent-komponent
    + Sette opp en "emitter" på child-komponent
    + Kjøre en funksjon som resultat av eventen og gjøre forandringer i reaktiv data. 

+ Lifecycle Hooks 
    + Forstå hva lifecycle hooks er 
    + Ha en oversikt over hooks som er tilgjenglig og når de kan brukes 
    + Sette opp en mounted 
    
    
+ Computed property 
    + Forstå hva en computed property er og hvordan den kan brukes 
    + Forstå et godt område for å bruke computed properties 
    
+ Methods
    + Forstå hva methods er 
    + Forstå hva strukturen for methods er
    + Forstå når man skal bruke methods
    + Forstå modularitet prinsippet og decoupling av methoder
    + Dependency injection prinsippet i method call 

+ beforeMount 
    + Forstå når man skal gjøre kall på API 
    + Bruke beforeMount til å populerer data objekter fra API 
        + Gjøre et kall til en async metode og await før man går videre

+ destroyed
    + Forstå når man skal bruke denne hooken til å rydde opp i observers og andre memory leaks 
    
+ Slots
    + Forstå hva slots brukes til 
    + Forstå hvordan man kan ha multiple slots med å gi dem navn 




+ Ha en god oversikt over vue direktives og short hands for vue APIet e.g. `v-bind === : && v-on === @`


## Mer avansert forståelse 
+ Forstå hvordan man bruker Vue DevTools og hvor viktig det er for debugging og utvikling 

+ Bruke axios som http klient for å kommuniserer med API
    + Installere axios 
    + Hente ut data fra et API
    + Sende data til et API 
    
+ Bruke VueRouter til å route rundt i samme applikasjon 
    + Forstå fordelene med single applikasjon (laster ned engang, kjører på klientet og bruker ressurser der)
    + Installere VueRouter
    + Sette opp en router 
    + Registrere router med Vue
    + Navigerer til forskjellige sider 
    + Forstå `before.router` hooken og hva den kan brukes til 
    + Forstå hvordan man bruker `<router-link>`
    + Forstår hvordan man bruker `<router/>`
    + Forstå hvordan man passer parametere, og når det er relevant, e.g. navigerer til /produkt/2 
    

+ Forstå hva Vuex Store er, og hvordan man bruker det med VueJS
    + Installerer Vuex Store
    + Sette opp config
    + Forstå hvorfor man aldri skal forandre data direkte, men gå gjennom en dispatch eller commit 
    + Dispatche til vuex store 
    + Bruke vuex store i en komponent
    + Mappe en data property fra vuex store til en komponent 
    + Forstå modul basert vuex store 
    
    
+ Sette opp Webpack basic config får å jobbe sammen med VueJS og Symfony


+ Forstå hvordan man inkluderer andre pakker med Vue.use() API
    + Sette opp vue-modals å teste ut hvordan det fungerer 

+ Forstå hvordan man kan binde ting til global window 
    + Binde axios til window objektet


## JS spesifikk forståelse 
+ Async await 
    + Forstå hvorfor man bruker async await 
    + Forstå hvordan man kan assigne en variable til en Promise callback
    + Forstå at async await er syntax sugar for Promise - Resolve 

+ Forstå `this` keyword 
+ Forstå `super` keyword
+ Dot notation `object.property` er det samme som `object->property` i PHP

  