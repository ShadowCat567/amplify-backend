## API Report File for "@aws-amplify/auth-construct"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { AuthOutput } from '@aws-amplify/backend-output-schemas';
import { AuthResources } from '@aws-amplify/plugin-types';
import { aws_cognito } from 'aws-cdk-lib';
import { BackendOutputStorageStrategy } from '@aws-amplify/plugin-types';
import { Construct } from 'constructs';
import { IFunction } from 'aws-cdk-lib/aws-lambda';
import { NumberAttributeConstraints } from 'aws-cdk-lib/aws-cognito';
import { ResourceProvider } from '@aws-amplify/plugin-types';
import { SecretValue } from 'aws-cdk-lib';
import { StandardAttributes } from 'aws-cdk-lib/aws-cognito';
import { StringAttributeConstraints } from 'aws-cdk-lib/aws-cognito';
import { UserPoolIdentityProviderSamlMetadata } from 'aws-cdk-lib/aws-cognito';
import { UserPoolSESOptions } from 'aws-cdk-lib/aws-cognito';

// @public
export type AmazonProviderProps = Omit<aws_cognito.UserPoolIdentityProviderAmazonProps, 'userPool' | 'attributeMapping'> & IdentityProviderProps;

// @public
export class AmplifyAuth extends Construct implements ResourceProvider<AuthResources> {
    constructor(scope: Construct, id: string, props?: AuthProps);
    readonly resources: AuthResources;
}

// @public
export type AppleProviderProps = Omit<aws_cognito.UserPoolIdentityProviderAppleProps, 'userPool' | 'attributeMapping'> & IdentityProviderProps;

// @public
export type AttributeMapping = {
    [K in keyof Omit<aws_cognito.AttributeMapping, 'custom'>]: string;
} & {
    custom?: {
        [key: string]: string;
    };
};

// @public
export type AuthProps = {
    name?: string;
    loginWith: {
        email?: EmailLogin;
        phone?: PhoneNumberLogin;
        externalProviders?: ExternalProviderOptions;
    };
    senders?: {
        email?: Pick<UserPoolSESOptions, 'fromEmail' | 'fromName' | 'replyTo'> | CustomEmailSender;
        sms?: UserPoolSnsOptions | CustomSmsSender;
    };
    userAttributes?: UserAttributes;
    multifactor?: MFA;
    accountRecovery?: keyof typeof aws_cognito.AccountRecovery;
    groups?: string[];
    outputStorageStrategy?: BackendOutputStorageStrategy<AuthOutput>;
};

// @public
export type CustomAttribute = CustomAttributeString | CustomAttributeNumber | CustomAttributeBoolean | CustomAttributeDateTime;

// @public
export type CustomAttributeBase = {
    mutable?: boolean;
};

// @public
export type CustomAttributeBoolean = CustomAttributeBase & {
    dataType: 'Boolean';
};

// @public
export type CustomAttributeDateTime = CustomAttributeBase & {
    dataType: 'DateTime';
};

// @public
export type CustomAttributeNumber = CustomAttributeBase & NumberAttributeConstraints & {
    dataType: 'Number';
};

// @public
export type CustomAttributeString = CustomAttributeBase & StringAttributeConstraints & {
    dataType: 'String';
};

// @public
export type CustomEmailSender = {
    handler: IFunction;
    kmsKeyArn?: string;
};

// @public
export type CustomSmsSender = {
    handler: IFunction;
    kmsKeyArn?: string;
};

// @public
export type EmailLogin = true | EmailLoginSettings;

// @public
export type EmailLoginSettings = (VerificationEmailWithLink | VerificationEmailWithCode) & {
    userInvitation?: {
        emailSubject?: string;
        emailBody?: (username: () => string, code: () => string) => string;
        smsMessage?: (username: () => string, code: () => string) => string;
    };
};

// @public
export type ExternalProviderOptions = {
    google?: GoogleProviderProps;
    facebook?: FacebookProviderProps;
    loginWithAmazon?: AmazonProviderProps;
    signInWithApple?: AppleProviderProps;
    oidc?: OidcProviderProps[];
    saml?: SamlProviderProps;
    scopes?: ('PHONE' | 'EMAIL' | 'OPENID' | 'PROFILE' | 'COGNITO_ADMIN')[];
    callbackUrls: string[];
    domainPrefix?: string;
    logoutUrls: string[];
};

// @public
export type FacebookProviderProps = Omit<aws_cognito.UserPoolIdentityProviderFacebookProps, 'userPool' | 'attributeMapping'> & IdentityProviderProps;

// @public
export type GoogleProviderProps = Omit<aws_cognito.UserPoolIdentityProviderGoogleProps, 'userPool' | 'clientSecretValue' | 'clientSecret' | 'attributeMapping'> & {
    clientSecret?: SecretValue;
} & IdentityProviderProps;

// @public
export type IdentityProviderProps = {
    attributeMapping?: AttributeMapping;
};

// @public
export type MFA = {
    mode: 'OFF';
} | ({
    mode: 'OPTIONAL' | 'REQUIRED';
} & MFASettings);

// @public
export type MFASettings = {
    totp?: MFATotpSettings;
    sms: MFASmsSettings;
} | {
    totp: MFATotpSettings;
    sms?: MFASmsSettings;
};

// @public
export type MFASmsSettings = boolean | {
    smsMessage: (createCode: () => string) => string;
};

// @public
export type MFATotpSettings = boolean;

// @public
export type OidcProviderProps = Omit<aws_cognito.UserPoolIdentityProviderOidcProps, 'userPool' | 'attributeRequestMethod' | 'attributeMapping'> & {
    readonly attributeRequestMethod?: 'GET' | 'POST';
} & IdentityProviderProps;

// @public
export type PhoneNumberLogin = true | {
    verificationMessage?: (createCode: () => string) => string;
};

// @public
export type SamlProviderProps = Omit<aws_cognito.UserPoolIdentityProviderSamlProps, 'userPool' | 'metadata' | 'attributeMapping'> & {
    metadata: Omit<UserPoolIdentityProviderSamlMetadata, 'metadataType'> & {
        metadataType: 'URL' | 'FILE';
    };
} & IdentityProviderProps;

// @public
export type TriggerEvent = (typeof triggerEvents)[number];

// @public
export const triggerEvents: readonly ["createAuthChallenge", "customMessage", "defineAuthChallenge", "postAuthentication", "postConfirmation", "preAuthentication", "preSignUp", "preTokenGeneration", "userMigration", "verifyAuthChallengeResponse"];

// @public
export type UserAttributes = StandardAttributes & Record<`custom:${string}`, CustomAttribute>;

// @public
export type UserPoolSnsOptions = {
    readonly externalId?: string;
    readonly snsCallerArn?: string;
    readonly snsRegion?: string;
};

// @public (undocumented)
export type VerificationEmailWithCode = {
    verificationEmailStyle?: 'CODE';
    verificationEmailBody?: (createCode: () => string) => string;
    verificationEmailSubject?: string;
};

// @public (undocumented)
export type VerificationEmailWithLink = {
    verificationEmailStyle?: 'LINK';
    verificationEmailBody?: (createLink: (text?: string) => string) => string;
    verificationEmailSubject?: string;
};

// (No @packageDocumentation comment for this package)

```
