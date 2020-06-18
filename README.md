# sdk-js
Sdk for live video streaming with Sidemash Cloud in Javascript Typescript

## Installation
```bash 
yarn add sidemash-sdk 
yarn add @types/sidemash-sdk
```

## Configuration
First, log in your account and create an `AuthAccess` object to query Sidemash Cloud with API. On creation, you will have a token and a privateKey : Use them to initialize a Sidemash client.
```typescript 
import {SidemashClient, Auth} from "sidemash-sdk"

const sdm = SidemashClient(Auth({ token : "1234", privateKey: "secret" }))
```

## Usage 
### Nomenclature 
The is pretty staright forward, if You have a resource that you want to Get List Update Patch or Delete, the you should do `sdm.{resourceTypeCamelCase}.{operation}({operationArgs})`.


### Get resources
```typescript
sdm.streamSquare.get({ id: "1234" })
```

### List resources
```typescript 
sdm.streamSquare.list({ where: "createdTime:in:[Yesterday.14h, Yesterday.15h[" })
```
```typescript 
sdm.streamSquare.list({ orderBy: "createdTime:ASC,status:DESC" })
```

### Create resources
```typescript
import {StreamSquare} from "sidemash-sdk"

sdm.streamSquare.create({ size: StreamSquare.Size.S, isElastic: false })
```

### Update resources
```typescript 
sdm.streamSquare.update({ id : "1234", newSize:  StreamSquare.Size.M })
```

### Delete resources 
```typescript
sdm.streamSquare.delete({id: "1234" })
```

