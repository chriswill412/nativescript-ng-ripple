# Nativescript Angular Native Ripple Plugin

This plugin aims to bring a native (or close to native) ripple implementation on Android and iOS. The android version uses a `RippleDrawable` and conserves the previous background, as well as CSS styles.

This is heavily based on https://github.com/bradmartin/nativescript-ripple with some improvements:

* It doesn't override the CSS on Android anymore
* iOS ripple is closer to the Android ripple.
## Installation

```javascript
tns plugin add nativescript-ng-ripple
```

## Usage 

This will only work on Android Lollipop 5.0 or later and any version of iOS.

### Import the NgRippleModule

If you're using other modules that change the background (like https://github.com/Especializa/nativescript-ng-shadow), ensure to import it LAST, otherwise the Ripple background will be overwritten.

```	
import { NgRippleModule } from 'nativescript-ng-ripple';

@NgModule({
    imports: [
        NgRippleModule,
        // ...
    ],
    // ...
})
export class MyModule { }
```

### Use it in the templates:

**ENSURE TO BIND A TAP LISTENER, OR THIS WON'T WORK ON ANDROID**

```<Label ripple text="my label text" (tap)="tapfn()"></Label>```

```
<StackLayout ripple rippleColor="#00ff00" style="padding: 30; border-radius: 10;" (tap)="tapfn()">
<Label text="this is inside the layout!"></Label>
</StackLayout>
```

### Implementation details

On Android, if the view does not have a background, we assign a transparent one. Otherwise, turning the screen off and then on again makes the background the same as the mask color (black).
    
## License

Apache License Version 2.0, January 2004
