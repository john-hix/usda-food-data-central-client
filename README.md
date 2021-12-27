A TypeScript client for the (FDC food central API)[https://fdc.nal.usda.gov/],
generated from their OpenAPI 3.x spec.

After downloading the API definition (fdc_api.yml), the client library was
was created with the following command (Docker installation required as well):

```bash
docker run --rm \
  -v ${PWD}:/local \
  openapitools/openapi-generator-cli generate \
  -i /local/fdc_api.yaml \
  -g typescript-axios \
  -o /local/
```

Example usage:

```typescript
import { Configuration } from './configuration';
import {FDCApi} from './index';


const api: FDCApi = new FDCApi(new Configuration({
    apiKey: 'YOUR_API_KEY',
    basePath: 'https://api.nal.usda.gov/fdc'
}));

api.getFood('170989', 'abridged', [203,204])
.then((res) => console.log(res.data))
.catch((e) => console.log(e));

```

