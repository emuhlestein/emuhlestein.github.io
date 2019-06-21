---
title: This is my title
layout: post
---
### Hello World 

### Styling Primeng pTooltip
If you are apply CSS in your inside Component css file than it will not apply on the tooltip because tooltip is added in body root path. So you have to add css in Global Css file of your project which were located in your project src > assets > css Or you can also apply in src > assets > styles.scss. Use below css: .ui-tooltip .ui-tooltip-text {
  background-color: red !important;
}

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









