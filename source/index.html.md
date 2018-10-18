---
title: Delos

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:tech@layertech.io?Subject=API%20Access'>Request API Key</a>
  - <a href='https://layertech.io/'>By Layer Tech</a>


search: true
---

# Welcome to Delos

Welcome to the Delos API. Delos API provides an easy and fast way to interact with the Factom blockchain. 

# Authentication

Contact Layer Tech to obtain an API key to use Delos.

```bash
curl -u YOUR_API_KEY: api.delos.layertech.io/v1/endpoints
```

> Make sure to replace `YOUR_API_KEY` with your API key. Leave colon in place.

Delos uses API keys to allow access to the API. You can request an API key by contacting tech [AT] layertech.io.

<aside class="notice">When not using <code>-u</code> flag, use <code>curl -H "Authorization: bearer YOUR_API_KEY"</code> to set the authorization header.</aside>

# Endpoints


## Create a Chain

Creates a chain with supplied entry.

```shell
curl -X POST -H "Content-Type: application/json" \ 
  -d '{"ext_ids": ["example1", "example2"], "content": "examplecontent"}'
  "https://api.layertech.io/api/chains" \
  -u YOUR_API_KEY
```

> The above command returns JSON structured like this:

```json
{
  "chain_id": "99268f3ad86eca2411115569e0c9e08f7cf7c642446553e0593cecd351c27bd"
}
```


### HTTP Request

`POST https://api.layertech.io/v1/chains`








## Create an Entry 

Creates an entry on specified chain.

```shell
curl -X POST -H "Content-Type: application/json" \ 
  -d '{"ext_ids": ["example1", "example2"], "content": "examplecontent"}'
  "https://api.layertech.io/api/chains/6e4540d08d5ac6a1a394e982fb6a2b8b516ee751c37420055141b94fe070bfe/entries" \
  -u YOUR_API_KEY
```

> The above command returns JSON structured like this:

```json
{
  "entry_hash": "82ffbc0976c70e987353f38219758af56d7598dc83c67653701f0f19b25b64e"
}
```


### HTTP Request

`POST https://api.layertech.io/v1/chains/<CHAIN_ID>/entries`








## Get Entries

If there are problems retrieving all entries, supply a limit or search term for ext id.

```shell
curl "https://api.layertech.io/v1/chains/6e4540d08d5ac6a1a394e982fb6a2b8b516ee751c37420055141b94fe070bfe/entries" \
  -u YOUR_API_KEY:
```


> The above command returns JSON structured like this:

```json
[
  {
    "chain_id": "6e4540d08d5ac6a1a394e982fb6a2b8b516ee751c37420055141b94fe070bfe",
    "entry_hash": "82ffbc0976c70e987353f38219758af56d7598dc83c67653701f0f19b25b64e",
    "content": "examplecontent",
    "external_ids": ["example1", "example2"]
  }
]
```

This endpoint retrieves a specific chain.

### HTTP Request

`GET https://api.layertech.io/v1/chains/<CHAIN_ID>/entries`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 500 | Gets up to the limit number of entries.
query | "" | Searches entries for ext id










## Get Entry

Gets entry data when given chain id and entry hash.

```shell
curl "https://api.layertech.io/v1/chains/6e4540d08d5ac6a1a394e982fb6a2b8b516ee751c37420055141b94fe070bfe/entries/82ffbc0976c70e987353f38219758af56d7598dc83c67653701f0f19b25b64e" \
  -u YOUR_API_KEY:
```


> The above command returns JSON structured like this:

```json
{
  "chain_id": "6e4540d08d5ac6a1a394e982fb6a2b8b516ee751c37420055141b94fe070bfe",
  "entry_hash": "82ffbc0976c70e987353f38219758af56d7598dc83c67653701f0f19b25b64e",
  "content": "examplecontent",
  "external_ids": ["example1", "example2"]
}
```

This endpoint retrieves a specific chain.

### HTTP Request

`GET https://api.layertech.io/v1/entries/<ENTRY_ID>`



