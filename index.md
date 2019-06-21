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
