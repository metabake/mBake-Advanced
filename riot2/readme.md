## Guidelines as to when to use Tag/Components

- Main point of page/screen should be pug/include, not a component - so it's easy to see what a page does
- But there are things around the main thing supporting it. Those could be tags. If:
- There is some .js that we can hide in the tag
- Could host the tag.js outside of the web app, think:  banner ad. Encapsulation! 
- Normally each tag, when mounted on the page, is passed the modelview. Binding is inside the tag.  eg: options
- Tag does update() (using virtual DOM as is current fad)
- When possible make tag as much attribute or dom based. eg yield, and again ... attributes over .js
- CSS style could be scoped -  Scoped CSS :scope
- Could be used in another webapps. eg: contact us.
- There could be multiple instance of a tag on a page.
- Leverage tag lifecycle events (eg mount) as needed.
- Avoid tag mixins. 
- *RULE* Must use Contexted DOM selector|query (check RIOT Guide for jq and w/o  jq)
- Tag should not reference or affect other things on a page. It is one way communication from page. If anything: tag broadcasts events
 


## Riot2 XXX Fix docs, move tags to folder.

The <yield> tag is a special riot core feature that allows you to inject and compile the content of any custom tag inside its template in runtime.

In this example `html` which is passed to a `tag` from `index.pug` specified under the `boa-tag` tag (the `form`):

```html
boa-tag
    form
        input(type='number', placeholder='Enter any number', id='one')
        input(type='number', placeholder='Enter any number', id='two')
        button(type='submit') Check sum!
```

And this `html` in compiled output will be inserted exactly in the place where the `<yield/>` tag is specified:

```html
    boa-tag

        p A simple example of calculating. The form below is passed inside a tag using Yield feature
        p.num { num }

        <yield />
```