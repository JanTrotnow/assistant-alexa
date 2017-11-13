## assistant-alexa
This package integrates Amazon Alexa into [AssistantJS][1]. Just install it with `npm install assistant-alexa --save` and add it as an dependency to your `index.ts`:
```typescript
import { descriptor as alexaDescriptor } from "assistant-alexa";

/** and below, in your "initializeSetups" method: */
assistantJs.registerComponent(alexaDescriptor);
```
This component also integrates a generator into AssistantJS. So, executing `assistant g`, creates a alexa-specific build in your `builds` directory.

### Configuration
Possible configuration options, as listed in our [interfaces.ts](src/components/alexa/interfaces.ts):
```typescript
export interface OptionalConfiguration {
  /** Route of alexa requests. Defaults to "/alexa". */
  route?: string;

  /** Mapping of slot values. Use your AssistantJS slot type as key and your alexa slot type as value. */
  parameters?: { [name: string]: string };

  /** If set to false, we will not use alexa-verifier to test valid requests. Using false might be useful for alexa simulator. Defaults to true. */
  useVerifier?: boolean;
};

export interface Configuration extends OptionalConfiguration {
  /** Your amazon alexa application id */
  applicationID: string;
};
```
As you can see, you need to configure your amazon alexa `applicationID` in order to use assistant-alexa. 

#### Debugging OAuth
If you start your AssistantJS server with `FORCED_ALEXA_OAUTH_TOKEN="mytoken"`, all alexa requests will return "mytoken" as OAuth token. 
That way, you can test or demo your skill without having a full OAuth setup in place.

[1]: http://assistantjs.org
