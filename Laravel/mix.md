# Laravel Mix

## Issues

### Dynamic import, VueJS component styling not working

* laravel-mix: 5.0.1

You might encounter this error after you finish compiling using command `npm run dev` or `npm run prod` and run your site in browser

```

Reason: TypeError: Cannot read property 'call' of undefined


```

Solution:

There is no fix right now, need to wait for webpack 5. If you intent to use dynamic import within your project, your VueJS Component must free from `<stye>` tag