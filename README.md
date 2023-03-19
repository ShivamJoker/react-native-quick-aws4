# react-native-quick-aws4

This library provides a fast implementation of AWS4 signing for React Native, built on top of [react-native-quick-crypto](https://github.com/username/react-native-quick-crypto) and [aws4-fetch](https://github.com/mhart/aws4fetch).

## Features

- Fast and efficient implementation of AWS4 signing for React Native.
- Built on top of [react-native-quick-crypto](https://github.com/margelo/react-native-quick-crypto) for high performance cryptographic operations.
- Easy to use API.

## Installation

### Quick-Crypto

This library requires the `react-native-quick-crypto` native module. Please ensure you have it setup by following the instructions [here](https://github.com/margelo/react-native-quick-crypto#installation).

### react-native-quick-aws4

Install the package using your preferred package manager.

```bash
yarn add react-native-quick-aws4
```

## Usage

Import the module wherever you want to use it.

```javascript
import { AwsClient } from "react-native-quick-aws4";
```

## Example

```javascript
import { AwsClient } from "react-native-quick-aws4";

const client = new AwsClient({
  accessKeyId: "YOUR_ACCESS_KEY_ID",
  secretAccessKey: "YOUR_SECRET_ACCESS_KEY",
  region: "us-east-1",
});

const payload = {
  functionName: "your-lambda-function-name",
  invocationType: "RequestResponse",
  payload: JSON.stringify({
    key1: "value1",
    key2: "value2",
    key3: "value3",
  }),
};

const res = await client.fetch(
  `https://lambda.us-east-1.amazonaws.com/2015-03-31/functions/${payload.functionName}/invocations`,
  {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: payload.payload,
  }
);

const result = await res.json();
console.log(result);
```
