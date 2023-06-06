![License](https://img.shields.io/badge/License-Apache%202.0-blue?style=flat-square)

# Portal JavaScript SDK

## Installation

```bash
npm install @kong/sdk-portal-js@latest # for latest version
```

## Usage

Below is some sample code, showing how to use the SDK to make a request to the Portal API. You can also look in the [`konnect-portal`](https://github.com/Kong/konnect-portal) repository for a more extensive example.

```ts
import {
  Configuration,
  PortalApi,
} from '@kong/sdk-portal-js'
import axios, { AxiosInstance } from 'axios'****

export default class PortalV2ApiService {
  private baseURL: string
  private client: AxiosInstance
  private portalAPI: PortalApi
  
  constructor (baseURL) {
    if (baseURL.endsWith('/')) {
      baseURL = baseURL.slice(0, -1)
    }
    
    this.client = axios.create({
      baseURL: this.baseURL,
      withCredentials: false,
      headers: {
        accept: 'application/json'
      }
    })
    
    const baseConfig = new Configuration({
      basePath: '',
      accessToken: 'bearerToken' 
    })
    
    this.portalAPI = new PortalApi(baseConfig, this.baseURL, this.client)
  }

// ...

// in your code
const portalAPI = new PortalV2ApiService('https://custom-portal.api.your-site.com')

// make a request to fetch details about the portal
const { data } = await portalAPI.portalAPI.getPortalInfo()
console.log(data)

```

## Requirements

- Node.js v16.19.0 or higher
- Axios

## Contributing

Currently this repository is automatically updated by an upstream repository containing the [Portal's OpenAPI Specification](https://developer.konghq.com/spec/2aad2bcb-8d82-43b3-abdd-1d5e6e84dbd6/b4539157-4ced-4df5-affa-7d790baee356). The changes are automatically opened here, and are manually merged and generated.

## License

```
Copyright 2016-2023 Kong Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```