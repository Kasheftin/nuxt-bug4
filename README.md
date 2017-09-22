# Please Help!

Mix of slot and nuxt-child breaks everything.

I've spent many hours to investigate the strange behavior in our large app.
Finally I've found it, it seems so furious that I just have no idea what to do next with nuxt and with our templates among the whole application.

As usual, I created the separate repo with very simple code to demonstrate it: https://github.com/Kasheftin/nuxt-bug4.
I'll show two bugs (alhough they may have one source).

I suppose the reason is this component we use as a wrapper:

```
<template>
  <div class="container">
    <div class="col -menu">
      <slot/>
    </div>
    <div class="col -content">
      <nuxt-child/>
    </div>
  </div>
</template>
```

If the user goes to the index page, we show him menu column only through the index page that looks like:

```
<template>
  <TwoColumns>
    MENU GOES HERE
  </TwoColumns>
</template>
```

Then he follows the nested route and the target page placed into the nuxt-child of the wrapper.

# The first bug:

1. Follow the /a link. There's an input field with v-model, type anything and it appears just after the input.
2. Follow /a/b link. Type something into the input field. It will work, but after every keypress nuxt show the progress bar at the top of the page like it load something. Although that's just simple inner component value update.

# The second bug:

3. Now follow /a/b/c link. Now only the first key press works. After that the data stops updating. It seems the component dies after the first key press. Although /b and /c are just nested nuxt-childs without javascript at all. And only the buggy progress bar at the top keeps working.
