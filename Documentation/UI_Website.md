> Author: Odeh Vincent, Palak
>
> Email: palak@mersus.ie
>
> Version: 0.1

# Responsiveness

Some ways to handle responsiveness:

1. Angular Flex
2. Using media queries - The AA website is made responsive using media queries.

# Responsive Header 

The responsive header for Mersus Website was made using media query because it is more suitable and user friendly.
The current width and height was set for each device in order to have the consistency either on the phone, Tablet or desktop and other smaller devices.

## What worked

### Screen sizes

1. Tablet and other big devices 

   `@media screen and (max-width: 768px)` 

2. Smaller devices 

   `@media screen and (max-width: 390px)`

### Sticky Header

#### CSS

Header was made sticky using the following CSS configuration: -

```scss
.fixed{
position: fixed;
width: 100%;
transition: 0.2s linear;
background: #0F2345;
margin: 0;
margin-right: 570px;
}
.fixed a {
margin-right: 40px;
font-family: 'Libre' 'Franklin';
font-weight: 20;
  }
```

#### Angular

Angular classes could be manipulated based on a certain criteria. The following was placed inside navbar and was styled in a different CSS.
 `(scroll)="onscroll()" [ngClass]="navbarfixed?'fixed':'notfixed'"`

#### Typescript

For the Typescript file, the following was implemented:

```typescript
export class HeaderComponent implements OnInit {
  navbarfixed:boolean =false;
@HostListener('window:scroll',['$event']) onscroll(){
 if(window.scrollY > 100){
   this.navbarfixed =true;
 }
 else{
   this.navbarfixed = false;
 }
}
```

### Navbar and logo

In order to fit the screens and make it more user friendly, the navbar and logo sizes were reduced. 

```scss
nav .logo {
    float: none;
    width: auto;
    justify-content: center;
}
```

`float:none;` - > To resize the font-size and width and height and were place to hide in a hamburger menu.

- The stick and transparent header were removed from the Tablet screen size. 

  ```scss
  .fixed{
    display: none;
    position: fixed;
    transition: 0.2s linear;
    background: #0F2345;
    margin: 0;
  }
  ```

- The hero image/video was set to a width of 100% and auto play.

  ```html
  <video  loop autoplay  class="back-video">
  <source src="/assets/AVA_website_header_v1.mp4" type="video/mp4">
  </video>

  .back-video{
      width: 100%;
  }
  ```

- The top header displaying the contact number and email were set to display none. 

```scss
.top {
    display: none;
}
```

#### Hover bounce Text animation

##### HTML

```html
    <div class="under"><li>About</li></div>
    <li><a href="#">Our Team</a></li>
    <li><a href="#">Project</a></li>
    <li><a href="#">Blog</a></li>
    <li><a href="#">Contact</a></li>
```
##### CSS

    /* Underline text for navbar */
    
    .under li a{
    
    text-decoration-line: underline; 
    }
    /* The animation Hover */
    .links a:hover{
    
    animation: bounce 1s linear;
    /* The animation Hover  */
    
    @keyframes bounce {
    
    0%,20%,60%,100%,to{  
         transform: translateY(0);
    }
    40%{
        transform: translateY(-30px);
    }
    70%{
        transform: translateY(-15px);
    }
    90%{
        transform: translateY(-4px);
    }
    }
### Hamburger menu

For tablet of smaller screens, a hamburger menu was created which allowed the navbar to go in and only display when clicked.

- Only visible for smaller screens
- Hamburger menu specific code: -

```scss
nav .icon-burger {
    display: block;
}
nav :checked ~ .icon-burger .line:nth-child(1) {
    transform: translateY(10px) rotate(225deg);
}
nav :checked ~ .icon-burger .line:nth-child(3) {
    transform: translateY(-10px) rotate(-225deg);
}
nav :checked ~ .icon-burger .line:nth-child(2) {
    opacity: 0;
}
```

- For smaller screens, some additional styling (like font, width, height, padding, margin, etc.) was done to fit the UI.  


- Some elements were made invisible for smaller screens, could be achieved by the following:

```scss
.row .top{

display:none;

}
```

