# Login

<!-- DOCS-IGNORE:start -->
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-0-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->
<!-- DOCS-IGNORE:end -->

The VTEX Login app handles user login in your store.

![login-component-gif](https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/images/vtex-login-0.gif)

## Configuration

1. Add the Login app to your theme dependencies in the `manifest.json` file:

```diff
  "dependencies": {
+   "vtex.login": "2.x"
  }
```

Now, you can use all the blocks exported by the Login app. See the full list below:

|   Block name    |                                                                                    Description                                                                                    |
|:---------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|     `login`     | ![https://img.shields.io/badge/-Mandatory-red](https://img.shields.io/badge/-Mandatory-red) Renders the Login component, as shown above. |
| `login-content` |                                                                           Only renders the login form.                                                                            |

2. Add the `login` block and its props to your store header. For example:

```json
"login": {
  "props": {
    "emailAndPasswordTitle": "LOG-IN",
    "accessCodeTitle": "Acess Code LOG-IN",
    "emailPlaceholder": "e-mail",
    "passwordPlaceholder": "password",
    "showPasswordVerificationIntoTooltip": true,
  }
}
```

### `login` props

|               Prop name               |    Type    |                                                                                                                                Description                                                                                                                                | Default value |
|:-------------------------------------:|:----------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------:|
|            `optionsTitle`             |  `string`  |                                                                                                                       Title text for login options.                                                                                                                       |  `undefined`  |
|        `emailAndPasswordTitle`        |  `string`  |                                                                                                        Text that will display with the email and password option.                                                                                                         |  `undefined`  |
|           `accessCodeTitle`           |  `string`  |                                                                                                            Text that will display with the access code option.                                                                                                            |  `undefined`  |
|          `emailPlaceholder`           |  `string`  |                                                                                                       Text that will display as a placeholder for the email input.                                                                                                        |  `undefined`  |
|         `passwordPlaceholder`         |  `string`  |                                                                                                      Text that will display as a placeholder for the password input.                                                                                                      |  `undefined`  |
|        `acessCodePlaceholder`         |  `string`  |                                                                                                    Text that will display as a placeholder for the access code input.                                                                                                     |  `undefined`  |
| `showPasswordVerificationIntoTooltip` | `boolean`  |                                                                                 Determines whether a tooltip for checking the password format should be shown (`true`) or not (`false`).                                                                                  |    `true`     |
|           `showIconProfile`           | `boolean`  |                                       Determines whether the `hpa-profile` icon from [Store Icons](https://developers.vtex.com/docs/guides/vtex-store-icons/) should be displayed in the Login component (`true`) or not (`false`).                                       |    `true`     |
|              `iconLabel`              |  `string`  |                                                                                                                      Title text for the Login icon.                                                                                                                       |  `undefined`  |
|            `hideIconLabel`            | `boolean`  |                                                                                 Determines whether the text string defined for the Login icon should be hidden (`true`) or not (`false`).                                                                                 |    `false`    |
|            `labelClasses`             | `[string]` |                                                                                                                          Login icon classnames.                                                                                                                           |  `undefined`  |
|     `providerPasswordButtonLabel`     |  `string`  |                                                                                                           Text that will display as the password button label.                                                                                                            |  `undefined`  |
| `hasIdentifierExtension` | `boolean` | Whether the identifier extension configurations should be enabled (`true`) or not (`false`). For more information, see the Advanced Configuration section below. | `true` |
|        `identifierPlaceholder`        |  `string`  |                                                                                                     Text that will display as a placeholder for the extension input.                                                                                                      |  `undefined`  |
|       `invalidIdentifierError`        |  `string`  |                                                                                                                Error message for invalid user identifier.                                                                                                                 |  `undefined`  |
|        `mirrorTooltipToRight`         | `boolean`  |                                                                                     Whether the Login tooltip should open on the right side of the screen (`true`) or not (`false`).                                                                                      |    `false`    |
|         `logInButtonBehavior`         |   `enum`   |                                                     Expected behavior of the Login component when clicked. Possible values are: `popover` (opens a popover tab) and `link` (redirects the user to the `/login` page).                                                     |   `popover`   |
|    `accountOptionsButtonBehavior`     |   `enum`   |                                                   Expected behavior of the My account button when clicked. Possible values are: `popover` (opens a popover tab) and `link` (redirects the user to the `/account` page).                                                   |   `popover`   |
|         `accountOptionLinks`          | `[object]` |                                                         Creates a custom link to replace the `accountOptionsButtonBehavior` set default `link` value (`/account`). See below the available props for the object.                                                          |  `undefined`  |
|         `termsAndConditions`          |  `string`  |                                                                                              Text that will display below the login options regarding terms and conditions.                                                                                               |  `undefined`  |
|           `hasGoogleOneTap`           | `boolean`  |                     ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Determines whether the [Google One Tap sign-up and auto sign-in](https://developers.google.com/identity/gsi/web/guides/overview) is displayed.                      |    `false`    |
|        `googleOneTapAlignment`        |   `enum`   |                      ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Defines the pop-up alignment for Google One Tap login. Possible values are `left` and `right`.                       |    `right`    |
|        `googleOneTapMarginTop`        |  `string`  | ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Defines the top margin for the Google One Tap login pop-up. The supported values are the same values supported by the CSS `top` property. |    `3rem`     |
|         `disabledEmailInputs`         | `boolean`  |                                                                                            Determines whether user email editing should be allowed (`true`) or not (`false`).                                                                                             |    `false`    |

> ⚠️ _Keep in mind that the Google One Tap props are still in beta. Although they are ready to be used, UX improvements should be expected._

- **`accountOptionLinks` object:**

| Prop name  |    Type    |           Description           | Default value |
|:----------:|:----------:|:-------------------------------:|:-------------:|
|  `label`   |  `string`  | Text label for the custom link. |  `undefined`  |
|   `path`   |  `string`  |        Custom link path.        |  `undefined`  |
| `cssClass` | `[string]` |     Login icon classnames.      |  `undefined`  |

### `login-content` props

|               Prop name               |   Type    |                                                                                         Description                                                                                         | Default value |
|:-------------------------------------:|:---------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------:|
|      `isInitialScreenOptionOnly`      | `boolean` |                                        Determines whether only the login options will be displayed on the initial screen (`true`) or not (`false`).                                         |    `true`     |
|            `defaultOption`            |  `enum`   | Defines the default login options that will be shown. Possible values are: `0` (shows the access code option), `1` (shows the email/password option), and `2` (shows the corporate option). |      `0`      |
|            `optionsTitle`             | `string`  |                                                                                Title text for login options.                                                                                |  `undefined`  |
|        `emailAndPasswordTitle`        | `String`  |                                                                 Text that will display with the email and password option.                                                                  |  `undefined`  |
|           `accessCodeTitle`           | `string`  |                                                                     Text that will display with the access code option.                                                                     |  `undefined`  |
|          `emailPlaceholder`           | `string`  |                                                                Text that will display as a placeholder for the email input.                                                                 |  `undefined`  |
|         `passwordPlaceholder`         | `string`  |                                                               Text that will display as a placeholder for the password input.                                                               |  `undefined`  |
| `showPasswordVerificationIntoTooltip` | `boolean` |                                          Determines whether a tooltip for checking the password format should be shown (`true`) or not (`false`).                                           |    `true`     |
|        `acessCodePlaceholder`         | `string`  |                                                             Text that will display as a placeholder for the access code input.                                                              |  `undefined`  |
|     `providerPasswordButtonLabel`     | `string`  |                                                                    Text that will display as the password button label.                                                                     |  `undefined`  |
| `hasIdentifierExtension` | `boolean` | Whether the identifier extension configurations should be enabled (`true`) or not (`false`). For more information, see the Advanced Configuration section below. | `true` |
|        `identifierPlaceholder`        | `string`  |                                                              Text that will display as a placeholder for the extension input.                                                               |  `undefined`  |
|       `invalidIdentifierError`        | `string`  |                                                                         Error message for invalid user identifier.                                                                          |  `undefined`  |
|         `termsAndConditions`          | `string`  |                                                       Text that will display below the login options regarding terms and conditions.                                                        |  `undefined`  |
|         `disabledEmailInputs`         | `boolean` |                                                     Determines whether user email editing should be allowed (`true`) or not (`false`).                                                      |    `false`    |

### Advanced configuration

By default, the email/password login asks two inputs from users:

- Email (_user identifier_)
- Password

You can set up the User Identifier Extension to allow other identifiers to be used in the Login form as long as they can be resolved to the user email in the background.

For example: If your account stores the national identity document of each user, the email/password login could be changed to ask for the following two inputs:

- National identity document (_user identifier_)
- Password

In order to display an identifier other than the user email, you have to create an **extension app** of your own to run in the background alongside the Login component.

The new extension app should be set up to receive the custom user identifier from the interface, such as the national identity document, and link it to the right user using store data. After that, the app should fetch the user email and return it to the Login app, which will behave as if the user had entered their email.

Below, you can find the instructions for running the User Identifier Extension in your store:

> ⚠️ Only enterprise clients can use this extension. You can check your account plan in your VTEX contract.

1. Make sure that the Login app is added as the extension app dependency and that the `store` builder is listed as one of its builders, as shown below:

```json
"dependencies": {
  "vtex.login": "2.x"
},
```

```json
"builders": {
  "store": "0.x",
},
```

2. [Develop a new component](https://vtex.io/docs/getting-started/desenvolva-componentes-usando-vtex-io-e-react/1) to replace the `email` input in the login form. This can be anything you want in its place, such as a file uploader or a simple text input which gets the national identity document.

When developing the component, remember that it must know how to convert the custom identifier to an email. This should be done by adding a callback function that returns an email within the Login app in the `react/{{ComponentName}}.js` file. For example:

```js
import { useState, useCallback, useEffect } from "react";

const ComponentName = ({
  renderInput,
  identifierPlaceholder,
  registerSubmitter,
}) => {
  // The component receives 3 props:
  // - renderInput is a function that returns the same input component used by the login app, defined in styleguide.
  //   It receives an object with three named parameters, trivially used by Inputs with react: value, onChange, placeholder.
  //   When "onChange" is called, the login app clears the "email is invalid" error, if it exists.
  // - identifierPlaceholder is the value of the configuration "identifierPlaceholder" defined in the storefront. It has a
  //   fallback to the value of the configuration "emailPlaceholder".
  // - registerSubmitter is a function that receives your async callback function defined in this file. Your callback will be called
  //   when the user submits the form.

  // This code controls the state of the rendered Input component.
  const [inputValue, setInputValue] = useState("");
  const onChangeInput = useCallback(
    (e) => setInputValue(e.target.value),
    [setInputValue]
  );

  // This callback function (onSubmit) should return the resolved email. In the example below, it adds `@email.com` to the current
  // value in the Input component (e.g.: "john" would be resolved to "john@email.com").
  const onSubmit = useCallback(async () => {
    const email = `${inputValue}@email.com`;
    return email;
  }, [inputValue]);

  // This code adds the async callback function you defined in the login app when this component mounts.
  useEffect(() => {
    registerSubmitter(onSubmit);
  }, [registerSubmitter, onSubmit]);

  // The component calls "renderInput" and renders its result.
  return renderInput({
    value: inputValue,
    onChange: onChangeInput,
    placeholder: identifierPlaceholder,
  });
};

export default ComponentName;
```

3. In the `store/interfaces.json` file, create a new [interface](https://developers.vtex.com/docs/guides/vtex-io-documentation-interface) for `user-identifier`, declaring the component you created in the previous step:

```json
"user-identifier.{{InterfaceName}}": {
  "component": "{{ComponentName}}"
},
```

> ℹ️ _The interface name, which is represented in the example above as `{{InterfaceName}}` can be anything your want._ ℹ️ _In the example above, the component created in step 2 is represented by `{{ComponentName}}`._

4. In the `store/plugins.json` file, add the new interface (`user-identifier`) for the Login app:

```json
"login > user-identifier": "user-identifier.{{InterfaceName}}",
"login-content > user-identifier": "user-identifier.{{InterfaceName}}",
```

> ℹ️ _If the `store/plugins.json` file is not available, you should create it._

> ⚠️ _Since the Login app behaves as if users were typing their emails, error messages like `The email is invalid` may appear even if the component is requesting other identifiers from users. This message, and others, can be edited in the Admin CMS._

## App behavior

The Login app reads the following query-string parameters:

- `returnUrl` - Redirects users to the given `returnUrl` once they are logged in. Caution: This parameter only works for the store domain and should be UTF-8 encoded (like javascript's `encodeURIComponent`).
- `oAuthRedirect` - Redirects users to the given OAuth provider page instead of displaying the native login options. For this to work, the given OAuth provider must be listed in the component as one of the login options. Caution: The parameter value is case-sensitive and must be `Google`, `Facebook`, or the name of the chosen OAuth provider.
- `userEmail` - User email information.
- `flowState` - Default state of the login flow. Possible values:
  - `createPass` - Sends an email to users with the code required to create a new password. Caution: When used, this parameter also requires the `userEmail` query string in the same URL.

> ℹ️ _Use the parameters above to build the desired Login URLs that will allow you to set the expected behavior for the component._

## Customization

In order to apply CSS customizations in this and other blocks, follow the instructions in the recipe for [Using CSS handles for store customization](https://developers.vtex.com/docs/guides/vtex-io-documentation-using-css-handles-for-store-customization).

|         CSS handles          |
|:----------------------------:|
|         `container`          |
|    `contentInitialScreen`    |
|     `contentFormVisible`     |
|          `profile`           |
|           `label`            |
|       `optionsSticky`        |
|        `optionsList`         |
|      `optionsListItem`       |
|  `optionsListItemContainer`  |
|    `accessCodeOptionBtn`     |
|   `emailPasswordOptionBtn`   |
|     `corporateOptionBtn`     |
|     `facebookOptionBtn`      |
|      `googleOptionBtn`       |
|    `customOAuthOptionBtn`    |
|       `oauthProvider`        |
|       `inputContainer`       |
|  `inputContainerAccessCode`  |
|   `inputContainerPassword`   |
|    `inputContainerEmail`     |
|     `emailVerification`      |
|         `emailForm`          |
|    `emailAndPasswordForm`    |
|     `forgotPasswordForm`     |
|     `formLinkContainer`      |
|          `arrowUp`           |
|         `buttonLink`         |
|         `formError`          |
|          `content`           |
| `content--emailVerification` |
| `content--emailAndPassword`  |
| `content--codeConfirmation`  |
|  `content--accountOptions`   |
| `content--recoveryPassword`  |
|           `button`           |
|         `sendButton`         |
|        `buttonSocial`        |
|        `buttonDanger`        |
|         `backButton`         |
|       `accountOptions`       |
|      `codeConfirmation`      |
|       `corporateEmail`       |
|         `formTitle`          |
|        `formSubtitle`        |
|            `box`             |
|      `contentContainer`      |
|         `formFooter`         |
|        `contentForm`         |
|  `contentAlwaysWithOptions`  |
|          `options`           |
|      `tooltipContainer`      |
|    `tooltipContainerTop`     |
|    `tooltipContainerLeft`    |
|   `loginOptionsContainer`    |
|     `termsAndConditions`     |
|     `forgotPasswordLink`     |
|      `dontHaveAccount`       |
|          `eyeIcon`           |

<!-- DOCS-IGNORE:start -->
## Contributors ✨

Thanks goes to these wonderful people:

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind are welcome!

<!-- DOCS-IGNORE:end -->
