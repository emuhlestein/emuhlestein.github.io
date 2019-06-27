
## Angular Notes
### Angular Module
An Angular module is a mechanism for combining components, services, directives and pipes. All the modules together combine to create an Angular application.

Here is an example of the most basic Angular module. The **NgModule** annotation or decorator is what marks a class as a module.
```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [ AppComponent ],
  imports: [ BrowserModule ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
The bootstrap component tells the compiler that this is the entry point for the app. There can technically be multiple bootstrap objects, but typically, there is only one.




Angular has a dependency injection registry. Any thing that is injectable is registered here.

### Angular Unit Tests



#### Creating mock object with three methods
mockHeroService = jasmine.createSpyObject(['getHeros', 'addHero', 'deleteHero'])
component = new HerosComponent(mockHeroService)

#### Add return type to method
// Have deleteHero method return an Observable that emits true

mockHeroService.deleteHero.and.returnValue(of(true))

#### Can call life cycle methods
component.ngOnInit()

component.delete(HEROES[2]); // deleting this hero should call the deleteHero method
// on the service. Hence this next expect:
expect(mockHeroService.deleteHero).toHaveBeenCalled();

it() is a jasmine test. xit(): prepending 'it' with 'x' makes it so the test does not run.
'x' is a note to Karma to ignore the test.

// test to make sure method was called with correct parameter
expect(mockHeroService.deleteHero).toHaveBeenCalledWith(HEREOS[2]);

### Testing Tips

1) Leave browser console open when running angular tests

2) ng test --source-map=false // not always recommended


### TestBed

TestBed is the main utility for testing angular components. In order to test, an angular module must be created. This is done using the TestBed.configureTestingModule() method. The argument to this method is an object that has values similar to NgModule:

```js
{
  imports: [],
  declarations: [],
  providers: []
}
```
As is the case with NgModule, these items are arrays of elements.

Here is an example for testing a simple component:
```
TestBed.configureTestingModule({
  declarations: [ SomeComponent ]
}).compileComponents();
```
This creates an testing module and caueses the test component, SomeComponent, to be compiled.
To get access to the component, the fixture must be retrieved. The fixture is the test environment for the component.

```
let component: SomeComponent;
let fixture: ComponentFixture<SomeComponent>;
...
fixture = TestBed.createComponent(SomeComponent);
component = fixture.componentInstance;
```


// create a HeroComponent and return a fixture component. This is just a wrapper around the actual component  
Allows a component and its template to be tested running together.  

The TestBed.configureTestingModule() creates an Angular module for testing purposes. It follows the same structure as an actual Angular module. The declarations section inclues the component that will be tested.

beforeEach(() => {
  TestBed.configureTestingModule({
  declarations: [HeroComponent],
  schemas: [NO_ERRORS_SCHEMA] // tell Angular that for this module, ignore unknown attributes and elements
  })
})

// This will create a component fixture which a wrapper for a component for testing.
fixture = TestBed.createComponent(HeroComponent);
The debug element is the rendered html.

The fixture is the test environment for the component.

~~~
TestBed.configureTestingModule({
  declarations: [ TheComponent],
 }).compileComponent(); // compiles the html and css
~~~

// get the actual component
component = fixture.componentInstance; //The actual component
de = fixture.debugElement; // For testing the rendered html

// create the hero property
component.hero = { id: 1, name: 'SuperDude', strength: 3 };
fixture.detectChanges(); // get angular to do binding, ie update any bindings that exist on the component

// get handle to anchor tag
fixture.nativeElement.querySelector('a');

// look for string, 'SuperDude', inside anchor tag
expect(fixture.nativeElement.querySelector('a').textContent).toContain('SuperDude'));

expect(de.query(By.css('h1)).nativeElement.innerText).toBe('The String');

{% highlight ruby linenos %}
// To test the value of a boolean: hideContent
it('should toggle', () => {
  expect(component.hideContent).toBeTruthy();
  component.toggle();
  expect(component.hideContent).toBeFalsy();
});

// To test the value of a boolean: hideContent. The method is now asynchronous
it('should toggle', fakeAsync(() => {
  expect(component.hideContent).toBeTruthy();
  component.toggleAsync();
  tick(500); // delay of 500ms
  expect(component.hideContent).toBeFalsy();
}));
{% endhighlight %}

fakeAsync() Create a fake angular zone that we can use to test asynchronous activity.
// nativeElement exposes the DOM API.

//debugElement is a wrapper around the DOM node.
// does same test as the one above
expect(fixture.debugElement.query(By.css('a')).nativeElement.textContent).toContain('SuperDude');

let deA = fixture.debugElement.query(By.css('a')); // debug element anchor tag (deA)
expect(deA.nativeElement.textContent).toContain('SuperDude');

// Get a handle to a service
let svc = TestBed.get(SomeService);

// When a component is constructed using the TestBed, **ngOnInit** will get called automatically.

During unit testing, components and services should be tested separately. Therefore, when testing a component, the injected
services should be mocked.

### Testing with a service that hits the backend
Do not want to use live data from the backend. This needs to be mocked.

~~~
let serviceStub: any; // The service stub or mock service

// usually done inside beforeEach()
serviceStub = {
  getContent: () => of('some message'); // The real object has this method
};

// The real service has a method called getContent()

TestBed.configureTestingModule({
  declarations: [ SomeComponent ],
  providers: [ { provide: MessageService, useValue: serviceStub } ]
~~~
When MessageSerivce is requested or injected, use serviceStyb instead. This is indicated by useValue.  
This tells the testing environment to use the serviceStub instead of the actual live data.

### Questions
1) What is an angular zone?
