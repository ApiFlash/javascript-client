# ApiFlash Javascript Client

Easily capture website screenshots using the ApiFlash [website screenshot API](https://apiflash.com). 

Signup at [apiflash.com](https://apiflash.com) to get your API key.

## Installation

```
npm install apiflash --save
```

## Example

```js
// TODO
console.log('ok');
```

Available parameters:

<table>
    <thead><tr><th>Parameter</th><th>Default</th><th>Description</th></tr></thead>
    <tbody>
        <tr>
            <td><kbd>access_key </kbd></td>
            <td></td>
            <td>Your personal access key to use the API. You can find it in your <a href="/dashboard/access_keys">dashboard</a>.</td>
        </tr>
        <tr>
            <td><kbd>url </kbd></td>
            <td></td>
            <td>The URL of the website you want to request a snapshot from. <span class="text-muted">The protocol (<code>http://</code> or <code>https://</code>) must be specified for the URL to be valid.</span></td>
        </tr>
        <tr>
            <td><kbd>ttl </kbd></td>
            <td><code>86400</code></td>
            <td>The number of seconds the screenshot should be kept in cache. When a screenshot is served from cache, the API call doesn't count in your monthly credit. From 0 to 2592000 <span class="text-muted">(30 days)</span> seconds.</td>
        </tr>
        <tr>
            <td><kbd>fresh </kbd></td>
            <td><code>False</code></td>
            <td>Return a fresh new screenshot instead of the eventually cached one.</td>
        </tr>
        <tr>
            <td><kbd>full_page </kbd></td>
            <td><code>False</code></td>
            <td>Set this to <code>true</code> if you want to capture the full height of the target website.</td>
        </tr>
        <tr>
            <td><kbd>scroll_page </kbd></td>
            <td><code>False</code></td>
            <td>Set this to <code>true</code> if you want the page to be scrolled through to trigger animations or lazy loaded elements.</td>
        </tr>
        <tr>
            <td><kbd>width </kbd></td>
            <td><code>1920</code></td>
            <td>Width of the viewport to use.</td>
        </tr>
        <tr>
            <td><kbd>height </kbd></td>
            <td><code>1080</code></td>
            <td>Height of the viewport to use. <span class="text-muted">This will be ignored if <kbd>full_page</kbd> is set to <code>true</code>.</span></td>
        </tr>
        <tr>
            <td><kbd>delay </kbd></td>
            <td><code>0</code></td>
            <td>Delay, after the <code>pageload</code> event is fired, to wait before taking the screenshot. From 0 to 10 seconds. <span class="text-muted">Most websites are fully loaded after the <code>pageload</code> event so this parameter is not needed most of the time.</span></td>
        </tr>
        <tr>
            <td><kbd>format </kbd></td>
            <td><code>jpeg</code></td>
            <td>The format of the returned screenshot. One of <code>jpeg</code> and <code>png</code>.</td>
        </tr>
        <tr>
            <td><kbd>response_type </kbd></td>
            <td><code>image</code></td>
            <td>
The type of response to return. Can be either <code>image</code> or <code>json</code>. <br/>
<span class="text-muted"><ul class="mt-2 mb-0"><li>If the response type is <code>image</code>, the binary data of the
screenshot is returned with the appropriate <code>Content-Type</code> and <code>Content-Length</code> headers.</li>
<li>If the response type is <code>json</code>, the response is a json document<span class="d-lg-none">.</span>
<span class="d-none d-lg-inline">formatted as follows:
<pre class="border rounded mt-2 mb-0"><code class="json">{
    "url": "https://url_of_screenshot_image...",
    "extracted_html": "https://url_of_extracted_html_here..."
}</code></pre></span></li></ul></span></td>
        </tr>
        <tr>
            <td><kbd>quality </kbd></td>
            <td><code>80</code></td>
            <td>The quality of the image between <code>0</code> and <code>100</code>. This only works with the <code>jpeg</code> format.</td>
        </tr>
        <tr>
            <td><kbd>transparent </kbd></td>
            <td><code>False</code></td>
            <td>Hides the default background and allows capturing screenshots with transparency. This only works with the <code>png</code> format.</td>
        </tr>
        <tr>
            <td><kbd>css </kbd></td>
            <td></td>
            <td>An additional CSS string to be injected into the page before capturing. <span class="text-muted">The CSS string might need to be URL encoded to be processed correctly.</span></td>
        </tr>
        <tr>
            <td><kbd>js </kbd></td>
            <td></td>
            <td>Additional JavaScript code to be injected into the page before capturing. For security reasons, this feature is disabled by default for all accounts. If you need it, please let us know. <span class="text-muted">The JS string might need to be URL encoded to be processed correctly.</span></td>
        </tr>
        <tr>
            <td><kbd>extract_html </kbd></td>
            <td><code>False</code></td>
            <td>Extract the HTML of the page at the same time the screenshot is made. This only works when the <kbd>response_type</kbd> parameter is set to <code>json</code>. When this parameter is set to <code>true</code>, an <code>extracted_html</code> attribute is added to the returned json document.</td>
        </tr>
        <tr>
            <td><kbd>accept_language </kbd></td>
            <td></td>
            <td>Sets an Accept-Language header on requests to the target URL allowing you to make screenshots of a website with a specific language.</td>
        </tr>
        <tr>
            <td><kbd>user_agent </kbd></td>
            <td></td>
            <td>Sets the User-Agent header to emulate a particular client when making screenshots.</td>
        </tr>
        <tr>
            <td><kbd>location </kbd></td>
            <td></td>
            <td>A country location to use when emulating geo-location. ISO alpha-2 and ISO alpha-3 country codes are supported.</td>
        </tr>
        <tr>
            <td><kbd>latitude </kbd></td>
            <td></td>
            <td>The latitude to use when emulating geo-location between <code>-90</code> and <code>90</code>.</td>
        </tr>
        <tr>
            <td><kbd>longitude </kbd></td>
            <td></td>
            <td>The longitude to use when emulating geo-location between <code>-180</code> and <code>180</code>.</td>
        </tr>
        <tr>
            <td><kbd>accuracy </kbd></td>
            <td><code>0</code></td>
            <td>Accuracy value to use when emulating geo-location.</td>
        </tr>
        <tr>
            <td><kbd>fail_on_status </kbd></td>
            <td></td>
            <td>A comma separated list of HTTP status codes that should make the API call fail instead of returning a screenshot. <span class="text-muted">Hyphen separated HTTP status codes can be used to define ranges. For example <code>400,404,500-511</code> would make the API call fail if the URL returns 400, 404 or any status code between 500 and 511.</span></td>
        </tr>
    </tbody>
</table>

