# Angular Universal routing issue

This repo is an example of a server side rendering routing issue.

This is a copy of the "finished sample code" from the angular.io guide: https://angular.io/guide/universal

# Description of error

In the app-routing.module.ts, when a route is added in the initialization of the routes variable, the route works. But if another route is pushed onto the array, it does _not_ work. 

The additional route is pushed on before the routes are added to the RouterModule, so I'm _not_ talking about adding dynamic routes later in the lifecycle.

# Commits

1. Direct unzip of the sample code, with the addition of this README, .gitignore and .prettierrc.  At this point, server and client rendering is working as expected.
1. Added /ping route and component. Server and client still working.
1. Added /broken-ping route. Server side broken; if started with ```ng serve``` it does work.
1. More docs

# Reproducing

## Positive

Run ```npm start``` to start the ng serve process. Browse to http://localhost:4200 and click around. 

Notice /ping and /broken-ping both work.

## Negative

Run ```npm run start:ssr``` (which is just a shortcut to the commands described at the bottom of the angular.io guide) and browse to http://localhost:4000

Notice the /ping works, but the /broken-ping does not work.

# Notes

- I inspected the /dist/server.js and things look the same for how 'ping' and 'broken-ping' are added to the routes
- The console.dir that outputs the routes at run time look exactly the same
- I have replicated this on a couple instances so far, but made this repo as the simpliest example I could make
