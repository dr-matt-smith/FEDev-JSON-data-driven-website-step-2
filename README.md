JSON-driven website: 
[Step 1](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-1)
|
[Step 2](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-2)
|
[Step 3](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-3)


# FEDev-JSON-data-driven-website-step-2

Step-by-step development of a module details website. Routing in the form `/module/2037`

## 1: extract the module code from the HTTP Request params

![module code extracted as as a heading](/screenshots/2_slug_extracted.png)

We can add a bit more to our catch-all module details page, to capture the module code from the URl

In `/routes/modules/[modulecode]/+page.svelte` we need to access the HTTP Request parameters
- through naming the directory `[modulecode]` we need to extract `modulecode` from the URL route parameters of this HTTP Request

We can write `export let params` statement to get access to the HTTP Request parameter data for a Sveltekit page script
- in our HTML code of the Svelte page we can then use `params.modulecode` to extract the route parameter `modulecode`

Update script `/routes/modules/[modulecode]/+page.svelte` to the following:

```html
<script>
    export let params;
</script>

<h1>
    You are looking for details of {params.modulecode}
</h1>

<p>
    module coming soon
    <br>
    <a href="/">
        &lt;-  back to home page
    </a>
</p>
```

If we wish, we could be a bit more organised, and put the code into its own variable `moduleCode`.
- this approach keeps our HTML code simpler, since we're referring to a simple variable name `{modulecode}` rather than `{params.modulecode}`
- although either approach is fine - write code that _you_ fully understand

`/routes/modules/[modulecode]/+page.svelte`
```html
<script>
    export let params;
    let moduleCode = params.modulecode
</script>

<h1>
    You are looking for details of {moduleCode}
</h1>

<p>
    module coming soon
    <br>
        <a href="/">
            &lt;-  back to home page
        </a>
</p>
```
