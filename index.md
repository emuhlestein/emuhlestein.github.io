---
title: This is my title
layout: post
---
### Hello World 

### Styling Primeng pTooltip
If you are apply CSS in your inside Component css file than it will not apply on the tooltip because tooltip is added in body root path. So you have to add css in Global Css file of your project which were located in your project src > assets > css Or you can also apply in src > assets > styles.scss. Use below css: .ui-tooltip .ui-tooltip-text {
  background-color: red !important;
}

### Angular

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

// create a HeroComponent and return a fixture component. This is just a wrapper around the actual component
fixture = TestBed.createComponent(HeroComponent);

// get the actual component
component = fixture.componentInstance;

// create the hero property
component.hero = { id: 1, name: 'SuperDude', strength: 3 };
fixture.detectChanges(); // get angular to do binding, ie update any bindings that exist on the component

// get handle to anchor tag
fixture.nativeElement.querySelector('a');

// look for string, 'SuperDude', inside anchor tag
expect(fixture.nativeElement.querySelector('a').textContent).toContain('SuperDude'));

// nativeElement exposes the DOM API.

//debugElement is a wrapper around the DOM node.
// does same test as the one above
expect(fixture.debugElement.query(By.css('a')).nativeElement.textContent).toContain('SuperDude');

let deA = fixture.debugElement.query(By.css('a')); // debug element anchor tag (deA)
expect(deA.nativeElement.textContent).toContain('SuperDude');

// Get a handle to a service
let svc = TestBed.get(SomeService);

// When a component is constructed using the TestBed, ngOnInit will get called automatically.

During unit testing, components and services should be tested separately. Therefore, when testing a component, the injected
services should be mocked.




