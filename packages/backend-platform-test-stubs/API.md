## API Report File for "@aws-amplify/backend-platform-test-stubs"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { CfnElement } from 'aws-cdk-lib';
import { Construct } from 'constructs';
import { ConstructContainer } from '@aws-amplify/plugin-types';
import { ConstructContainerEntryGenerator } from '@aws-amplify/plugin-types';
import { ConstructFactory } from '@aws-amplify/plugin-types';
import { ImportPathVerifier } from '@aws-amplify/plugin-types';
import { Stack } from 'aws-cdk-lib';

// @public
export class AmplifyStackStub extends Stack {
    allocateLogicalId: (element: CfnElement) => string;
}

// @public
export class ConstructContainerStub implements ConstructContainer {
    constructor(stackResolver: StackResolver);
    getConstructFactory: <T>(token: string) => ConstructFactory<T>;
    getOrCompute: (generator: ConstructContainerEntryGenerator) => Construct;
    registerConstructFactory: (token: string, provider: ConstructFactory) => void;
}

// @public
export class ImportPathVerifierStub implements ImportPathVerifier {
    // (undocumented)
    verify: () => void;
}

// @public
export type StackResolver = {
    getStackFor: (resourceGroupName: string) => Stack;
};

// @public
export class StackResolverStub implements StackResolver {
    constructor(rootStack: Stack);
    getStackFor: (resourceGroupName: string) => Stack;
}

// (No @packageDocumentation comment for this package)

```