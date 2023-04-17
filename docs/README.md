# Login

<!-- DOCS-IGNORE:start -->
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-0-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->
<!-- DOCS-IGNORE:end -->

The VTEX Login app is responsible for handling user login in your store. 

![login-component-gif](https://user-images.githubusercontent.com/52087100/99320783-21396580-284b-11eb-8a54-f64aa1cf7781.gif)

## Configuration

1. Add the Login app to your theme's dependencies in the `manifest.json` file:

```diff
  "dependencies": {
+   "vtex.login": "2.x"
  }
```

Now, you are able to use all the blocks exported by the Login app. Check out the full list below:

| Block name   | Description  |
| :----------: | :------------------------: |
| `login` | ![https://img.shields.io/badge/-Mandatory-red](https://img.shields.io/badge/-Mandatory-red) Renders the Login component, as shown in the media above. | 
| `login-content` | Only renders the login form . | 

2. Add the `login` block and its props to your store's header. For example:

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

|               Prop name               |    Type    |                                                                                                                            Description                                                                                                                             | Default value |
| :-----------------------------------: | :--------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------: |
|            `optionsTitle`             |  `string`  |                                                                                                                 Text to entitle the login options.                                                                                                                 |  `undefined`  |
|        `emailAndPasswordTitle`        |  `string`  |                                                                                                           Text to display the email-and-password option.                                                                                                           |  `undefined`  |
|           `accessCodeTitle`           |  `string`  |                                                                                                              Text to display the access-code option.                                                                                                               |  `undefined`  |
|          `emailPlaceholder`           |  `string`  |                                                                                                      Text to be displayed as placeholder to the email input.                                                                                                       |  `undefined`  |
|         `passwordPlaceholder`         |  `string`  |                                                                                                     Text to be displayed as placeholder to the password input.                                                                                                     |  `undefined`  |
|        `acessCodePlaceholder`         |  `string`  |                                                                                                   Text to be displayed as placeholder to the access code input.                                                                                                    |  `undefined`  |
| `showPasswordVerificationIntoTooltip` | `boolean`  |                                                                             Whether a tooltip responsible for checking the password format should be shown (`true`) or not (`false`).                                                                              |    `true`     |
|           `showIconProfile`           | `boolean`  |                                         Whether the `hpa-profile` icon from [Store Icons](https://developers.vtex.com/docs/guides/vtex-store-icons/) should be displayed on the Login component (`true`) or not (`false`).                                         |    `true`     |
|              `iconLabel`              |  `string`  |                                                                                                               Text string to entitle the Login icon.                                                                                                               |  `undefined`  |
|            `hideIconLabel`            | `boolean`  |                                                                                   Whether the text string defined for the Login icon should be hidden (`true`) or not (`false`).                                                                                   |    `false`    |
|            `labelClasses`             | `[string]` |                                                                                                                      Login icon's classnames.                                                                                                                      |  `undefined`  |
|     `providerPasswordButtonLabel`     |  `string`  |                                                                                                         Text to be displayed as the password button label.                                                                                                         |  `undefined`  |
|        `identifierPlaceholder`        |  `string`  |                                                                                                    Text to be displayed as placeholder to the extension input.                                                                                                     |  `undefined`  |
|       `invalidIdentifierError`        |  `string`  |                                                                                                             Error message for invalid user identifier.                                                                                                             |  `undefined`  |
|        `mirrorTooltipToRight`         | `boolean`  |                                                                               Whether the Login tooltip should open towards the right side of the screen (`true`) or not (`false`).                                                                                |    `false`    |
|         `logInButtonBehavior`         |   `enum`   |                                                  Expected behavior of the Login component when clicked on. Possible values are: `popover` (opens a popover tab) and `link` (redirects user to the `/login` page).                                                  |   `popover`   |
|    `accountOptionsButtonBehavior`     |   `enum`   |                                                Expected behavior of the My account button when clicked on. Possible values are: `popover` (opens a popover tab) and `link` (redirects user to the `/account` page).                                                |   `popover`   |
|         `accountOptionLinks`          | `[object]` |                                            Creates a custom link to replace the default one set for the `accountOptionsButtonBehavior`'s `link` value (`/account`). Check out below the available props for the object.                                            |  `undefined`  |
|         `termsAndConditions`          |  `string`  |                                                                                              Text to be displayed below the login options regarding terms&conditions.                                                                                              |  `undefined`  |
|           `hasGoogleOneTap`           | `boolean`  |                  ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Whether the [Google's One-tap sign-up and auto sign-in](https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/images/vtex-login-2.png).                  |    `false`    |
|        `googleOneTapAlignment`        |   `enum`   |                   ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Defines pop-up alignment for the Google One-tap login. Possible values are `Left` and `Right`.                   |    `Right`    |
|        `googleOneTapMarginTop`        |  `string`  | ![https://img.shields.io/badge/-Beta-red](https://img.shields.io/badge/-Beta-red) Defines the pop-up top margin for the Google One-tap login. The values supported are the same supported by the CSS property `top`. |    `3rem`     |
|         `disabledEmailInputs`         | `boolean`  |                                                                                              Whether user email editing should be allowed (`true`) or not (`false`).                                                                                               |    `false`    |
|       `blockOAuthAutoRedirect`        | `boolean`  |                                                 If this prop is `true` and the only active provider is an OAuth, the login won't auto-redirect as usual. Also, the query string `oAuthRedirect` will be disabled.                                                  |    `false`    |

> ⚠️ Notice that the Google One Tap props are still in Beta. Although they are ready to be used, UX improvements should be expected.

- **`accountOptionLinks` object:**

| Prop name  |    Type    |           Description           | Default value |
| :--------: | :--------: | :-----------------------------: | :-----------: |
|  `label`   |  `string`  | Text lable for the custom link. |  `undefined`  |
|   `path`   |  `string`  |       Custom link's path.       |  `undefined`  |
| `cssClass` | `[string]` |    Login icon's class names.    |  `undefined`  |

### `login-content` props

|               Prop name               |   Type    |                                                                                                    Description                                                                                                    | Default value |
| :-----------------------------------: | :-------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------: |
|      `isInitialScreenOptionOnly`      | `boolean` |                                                         Whether only the login options will be displayed on the initial screen (`true`) or not (`false`).                                                         |    `true`     |
|            `defaultOption`            |  `enum`   | Defines the default login options to be shown. Possible values are: `0` (shows the access-code option for login), `1` (shows the email/password option for login) and `2` (shows the corporate option for login). |      `0`      |
|            `optionsTitle`             | `string`  |                                                                                        Text to entitle the login options.                                                                                         |  `undefined`  |
|        `emailAndPasswordTitle`        | `String`  |                                                                                  Text to display the email-and-password option.                                                                                   |  `undefined`  |
|           `accessCodeTitle`           | `string`  |                                                                                      Text to display the access-code option.                                                                                      |  `undefined`  |
|          `emailPlaceholder`           | `string`  |                                                                              Text to be displayed as placeholder to the email input.                                                                              |  `undefined`  |
|         `passwordPlaceholder`         | `string`  |                                                                            Text to be displayed as placeholder to the password input.                                                                             |  `undefined`  |
| `showPasswordVerificationIntoTooltip` | `boolean` |                                                     Whether a tooltip responsible for checking the password format should be shown (`true`) or not (`false`).                                                     |    `true`     |
|        `acessCodePlaceholder`         | `string`  |                                                                           Text to be displayed as placeholder to the access code input.                                                                           |  `undefined`  |
|     `providerPasswordButtonLabel`     | `string`  |                                                                                Text to be displayed as the password button label.                                                                                 |  `undefined`  |
|        `identifierPlaceholder`        | `string`  |                                                                            Text to be displayed as placeholder to the extension input.                                                                            |  `undefined`  |
|       `invalidIdentifierError`        | `string`  |                                                                                    Error message for invalid user identifier.                                                                                     |  `undefined`  |
|         `termsAndConditions`          | `string`  |                                                                     Text to be displayed below the login options regarding terms&conditions.                                                                      |  `undefined`  |
|         `disabledEmailInputs`         | `boolean` |                                                                      Whether user email editing should be allowed (`true`) or not (`false`).                                                                      |    `false`    |

### Advanced configuration

The email/password login asks by default two inputs from users:

- The email (_user identifier_)
- The password

It is possible to **set up the User Identifier Extension, allowing other identifiers to be used in the Login's form instead** - as long as they can be resolved to the user email behind the scenes.

For example: if your account stores the National Identity Document of each user, the email/password login could be changed to ask for the following two inputs:

- The National Identity Document (_user identifier_)
- The password

In order to display an identifier other than the user email, you must create an **extension app** of your own to work behind the scenes with the Login component.

The new extension app should be set up to receive the custom user identifier from the interface, such as the National Identity Document, and link it to the accurate user using the store data. Thereafter, the app should fetch the user email and return it to the Login app, which will behave as if the user just typed in their email.

Find below the needed instructions to perform the User Identifier Extension in your store:

> ⚠️ This extension is only allowed for enterprise clients. You can check your account plan in your VTEX contract.

1. Ensure that the Login app is added as your extension app's dependency and that the `store` builder is listed as one of its builders, as shown below:

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

2. [Develop a new component](https://vtex.io/docs/getting-started/desenvolva-componentes-usando-vtex-io-e-react/1) to replace the `email` input in the login form. It can be anything you desire for that position, such as a file uploader or a simple text input which takes the National Identity Document.

> When developing it, remember that it must know how to convert the custom identifier to an email. This should be done by registering a callback function, which returns an email within the Login app, in the `react/{{ComponentName}}.js` file. For example:

```js
import { useState, useCallback, useEffect } from "react";

const ComponentName = ({
  renderInput,
  identifierPlaceholder,
  registerSubmitter,
}) => {
  // The component receives 3 props:
  // - renderInput is a function that returns the same Input component used by the login app, defined in styleguide.
  //   It receives an object with three named parameters, trivially used by Inputs with react: value, onChange, placeholder.
  //   When "onChange" is called, the login app clears the "email is invalid" error, if it exists.
  // - identifierPlaceholder is the value of the configuration "identifierPlaceholder" defined in the Store Front. It has a
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
  // value in the Input component (eg. "john" would be resolved to "john@email.com").
  const onSubmit = useCallback(async () => {
    const email = `${inputValue}@email.com`;
    return email;
  }, [inputValue]);

  // This code registers the async callback function you defined in the login app when this component mounts.
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

3. In the `store/interfaces.json` file, create a new [interface](https://vtex.io/docs/getting-started/desenvolva-componentes-usando-vtex-io-e-react/4#entendendo-interfaces) for `user-identifier`, declaring the component you created in the previous step:

```json
"user-identifier.{{InterfaceName}}": {
  "component": "{{ComponentName}}"
},
```

> The interface name, which is represented in the example above as `{{InterfaceName}}`, can be any of your choosing.
> In the example above, the component created in the step 2 is represented by `{{ComponentName}}`.

4. In the `store/plugins.json` file, plug in the new interface (`user-identifier`) to the Login app:

```json
"login > user-identifier": "user-identifier.{{InterfaceName}}",
"login-content > user-identifier": "user-identifier.{{InterfaceName}}",
```

> If the `store/plugins.json` file is not available, you should create it.

> ⚠️ Since the Login app behaves as if users were typing their emails, error messages like `The email is invalid` may appear even if the component is asking users other identifiers. This message, along with others, can be edited in the admin's CMS.

## Modus Operandi

The Login app reads the following query-string parameters:

- `returnUrl` - Redirects users to the given `returnUrl` once they are logged in. Caution: This parameter only works for the store's domain and should be UTF-8 encoded (as in javascript's `encodeURIComponent`).
- `oAuthRedirect` - Redirects users to the given OAuth Provider page, instead of displaying the native login options. For this to work, the given OAuth Provider must be listed on the component as one of the login options. Caution: The parameter value is case sensitive and must be `Google`, `Facebook` or the registered name of the chosen OAuth Provider.
- `userEmail` - User email data.
- `flowState` - Default state of the login flow. Possible values:
  - `createPass` - Sends an email to users with the code required to create a new password. Caution: When used, this parameter also requires the `userEmail` query string in the same URL.

> Use the parameters above to build the Login's desired URLs - through which you will be able to set the expected behavior for the component.

## Customization

In order to apply CSS customizations in this and other blocks, follow the instructions given in the recipe on [Using CSS Handles for store customization](https://developers.vtex.com/docs/guides/vtex-io-documentation-using-css-handles-for-store-customization).

|         CSS Handles          |
| :--------------------------: |
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
