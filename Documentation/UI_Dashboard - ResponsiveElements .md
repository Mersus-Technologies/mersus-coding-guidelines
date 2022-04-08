> Author: Palak
>
> Email: palak@mersus.ie
>
> Version: 0.1

# Responsiveness

For the Avatar Academy Dashboard, Desktop first approach was followed. It means that the Wireframes and development started for the desktop view and then were handled for other resolutions.

Some ways to handle responsiveness:

1. Angular Flex


- Can break resolutions in html and apply respective CSS (yet to find the best breakdown) and apply for all - Working for me atm
- Can add a breakpoint observer: [Managing Image Breakpoints With Angular — Smashing Magazine](https://www.smashingmagazine.com/2019/02/image-breakpoints-angular/)
- Bootstrap and Angular: [Detect Responsive Screen Sizes in Angular | DigitalOcean](https://www.digitalocean.com/community/tutorials/detect-responsive-screen-sizes-in-angular)

2. Using media queries (Used for Website)

# Responsiveness using Angular Flex

For the Avatar Academy Dashboard, the UI was made responsive using Angular flex.

**NPM link**: [@angular/flex-layout - npm](https://www.npmjs.com/package/@angular/flex-layout)

**Github link**: [GitHub - angular/flex-layout: Provides HTML UI layout for Angular applications; using Flexbox and a Responsive API](https://github.com/angular/flex-layout)

**Youtube tutorial:** 

Part 1: [Create a responsive card grid in Angular with Flex Layout - Part 1](https://youtu.be/O460xQPYckE)

Part 2: [Create a responsive card grid in Angular with Flex Layout - Part 2](https://youtu.be/C5ew4olWLGQ)

**Tutorial:**

[Angular Flex-Layout: The Alternative Layout Library for Flex-box and CSS Grid | by Duncan Faulkner | ngconf | Medium](https://medium.com/ngconf/angular-flex-layout-ddf1c8fad37e)

[How To Use Flex Layout for Angular | DigitalOcean](https://www.digitalocean.com/community/tutorials/angular-flex-layout)

[Getting started with Angular Flex-Layout - Excellarate](https://www.excellarate.com/blogs/getting-started-with-angular-flex-layout/)

The following steps could be helpful in managing responsiveness for common Angular elements. 

## Step 1: Identify breakdown

The components were configured for various resolutions while following the below Resolution breakdown:

**![img](https://lh4.googleusercontent.com/zrVhsHxmlB49WFZy8gmnueApxayNsh5XDtYLvrQH_Q7ljdbbtjLskq3QrNazVLXjwHZwuHoM7fz4jBN2hmQ7tLgI_wrlvjUS6ssQacm67s3CIlwpGMEkZE_KyHNioX_w_e-K5HkQ)**


General Angular flex resolution breakdown used in the Avatar Academy Dashboard (Worked well as per the wireframes)

`fxLayout.lt-md`
`fxLayout.lt-lg`

If needed, can specify for the particular resolution:
`fxFlex.md`

## Step 2: Configure CSS classes accordingly

For any further formatting required for an element for a particular resolution, configure a CSS class to manage that.

```html
class="card-config" //Default class

[ngClass.lt-lg] ="'card-column'"  //Class for less than large res
```

As far as I’ve experienced, flex can be configured for specific components as well. The next section contains a few elements that I came across.

# Angular (and otherwise) component specific

## Text

### What worked

Using vh (viewport height) and vw (viewport width)
Specifying properties for each resolution 

### Alternates

Using px, percent, etc.

## Mat card

This is especially useful to create a grid of cards.

**![img](https://lh6.googleusercontent.com/pJlLavnhNhAw8dJisn_QvyyrB0Kx8X9AYZNkllTpbbS3FWOQ5Mnciyec-sBgF1QXoDAdAXVlj8_-CmXaP5QD7hgdcRQUlFBWCMjT53oXRMrKBLFRDe2uj6CuBO8QKQJTrgat89uF)**

### What worked

Can find alternatives to mat-card if required but some predefined tags in HTML were handy (like mat-card-title, mat-card-content etc.)

The flex layout worked well for me to manage grids.
`fxLayout="row wrap"`

Row wrap turned out to be:

- Easier while dealing with responsiveness
- Requires less manual work for handling card grids for different resolutions as it can manage cards in rows and columns better as compared to other `fxLayouts` tried.

### Alternates

Can find more layouts here - [Angular Flex-Layout Demos](https://tburleson-layouts-demos.firebaseapp.com/#/docs)

## Responsive spinner circle

### What worked

[ng-circle-progress - npm](https://www.npmjs.com/package/ng-circle-progress)

**![img](https://lh3.googleusercontent.com/FEipoZcGZHKbLgbBXSKrQmPy_haGTdmXPqtl3fnLoWg2GVOQCEU_3Zynn_I9C-MqfC-UwqUFvh5kvxwR_fYWryTwMU731jyNKc9BvysBRF_zbTfV5ZCYhrskN9nBfpvQpuoYsO3O)**

**Pros:**

- 
  Interactive

- Contains predefined properties that can be configured
- Has better provisions for placing text/images in the middle, won’t need to place the circle and text separately
- Has animations
- Easy to make it responsive

**Cons:**

- Could be hard to find the correct property to configure

- If need to customize outside of the presets given, have to use ::ng-deep with the predefined class (or something else) to override the settings

### Alternates

[Progress spinner | Angular Material](https://material.angular.io/components/progress-spinner/api) - This was used before but it’s hard to manage the text and circle placements, especially while dealing with different resolutions.

## Table

### What worked

[Table | Angular Material](https://material.angular.io/components/table/overview)

Using mat-table and defining flex for each column as below

`.mat-column-ColumnName{`

`flex: 0 0 17%;`

`}`

`flex`: Flex-grow Flex-shrink Flex-basis
The `ColumnName` is the one specified in `matColumnDef`

### Alternates

Not explored enough yet.

# Useful links

[GitHub - angular/flex-layout: Provides HTML UI layout for Angular applications; using Flexbox and a Responsive API](https://github.com/angular/flex-layout)

[flex-layout/Responsive-API.md at master](https://github.com/angular/flex-layout/blob/master/docs/documentation/Responsive-API.md)
