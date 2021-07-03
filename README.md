###  Proxy using Cloudflare Workers <br><br>

####  Paste the Code: <br><br>

```
async function handleRequest(request) {
  const url = new URL(request.url)
  if (url.hostname in ORIGINS) {
    const target = ORIGINS[url.hostname]
    url.hostname = target
    return fetch(url.toString(), request)
  }
  return fetch(request)
}
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

const ORIGINS = {
  'resolver.domain': 'origin.domain'
}
```
<br><br>

**Replace 'resolver.domain' with '[Your choosed Worker Name].[Your Worker Subdomain]'**



    ## Example
    
    'github.duocodies.workers.dev'

<br>

**Replace 'origin.domain' with '[Origin Domain]'**

    ## Example
    
    'github.com'

<br><br>

#### The Code should be like this:<br>


    ## Example
	
    async function handleRequest(request) {
      const url = new URL(request.url)
      if (url.hostname in ORIGINS) {
        const target = ORIGINS[url.hostname]
        url.hostname = target
        return fetch(url.toString(), request)
      }
      return fetch(request)
    }
    addEventListener('fetch', event => {
      event.respondWith(handleRequest(event.request))
    })
    
    const ORIGINS = {
      'github.duocodies.workers.dev': 'github.com'
    }
    

<br><br>

>  This content has been shared under Educational Purposes Only. Developers not responsible for the actions performed by user
