# THEOplayer Angular Sample

## License

This projects falls under the license as defined in https://github.com/THEOplayer/license-and-disclaimer.

## Requirements:

A web SDK created at https://portal.theoplayer.com !
Make sure to keep your Library Location "https://cdn.XXX.theoplayer.com/YOUR_KEY_HERE" at hand. This can be found in the overview on the Portal of your freshly created SDK. Also download your 'THEOplayer.js' file by going to the following link: https://cdn.XXX.theoplayer.com/YOUR_KEY_HERE/THEOplayer.js

## Step-by-step guide:

Note that this information is for a basic player in a local testing environment. Additional information may be needed for specific cases.

1. Make sure you have the Angular CLI installed

```
npm install -g @angular/cli
```

2. If needed, create a new workspace and initial application
```
ng new appname
```

3. In the root project, create a new component for the player (in this case appname)

```
cd appname
ng generate component theoplayer
```
Note that we are using a project with CSS for the styling.

4. Add the THEOplayer.js file to the root of the project.
5. In index.html add the /THEOplayer.js as a script tag and /ui.css as a stylesheet. These should look something like this:
```
<link rel="stylesheet" type="text/css" href="https://cdn.XXX.theoplayer.com/YOUR_KEY_HERE/ui.css">
<script type="text/javascript" src='https://cdn.XXX.theoplayer.com/YOUR_KEY_HERE/THEOplayer.js'></script>

```
6. In theoplayer.component.html add:

```
<div class="theoplayer-container video-js theoplayer-skin"></div>
```

If you want to change the size of your player you could add the following to theoplayer.component.css
```
.theoplayer-container {
    width: 480px;
    height: 300px;
}
```

7. In theoplayer.component.ts add

```
import { Component, OnInit } from '@angular/core';
import * as THEOplayer from '../../../THEOplayer.js';

@Component({
  selector: 'app-theoplayer',
  templateUrl: './theoplayer.component.html',
  styleUrls: ['./theoplayer.component.css']
})
export class TheoplayerComponent implements OnInit {

  constructor() { }

  ngOnInit() {
    this.createPlayer();
  }

  createPlayer() {
    const element = document.querySelector('.theoplayer-container');

    const player = new THEOplayer.Player(element, {
      libraryLocation : 'https://cdn.XXX.theoplayer.com/YOUR_KEY_HERE'
    });

    player.source = {
     sources : [{
         src : '//cdn.theoplayer.com/video/elephants-dream/playlist.m3u8',
         type : 'application/x-mpegurl' // sets type to HLS
     }]
 };
  }
}
```

Make sure the following line is at the top:

```
import * as THEOplayer from '../../../THEOplayer.js;
```

This will make sure to get everything needed from our SDK.

9. In app.component.html add the following code to display the player in the app component.

```
<app-theoplayer></app-theoplayer>
```

10. THEOplayer should be configured!

## Related articles

https://angular.io/guide/quickstart
