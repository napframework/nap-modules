<br>
<p align="center">
  <img width=384 src="https://download.nap.tech/identity/svg/logos/nap_logo_blue.svg">
</p>

- [Description](#description)
  * [Register your Module](#register-your-module)
    + [Description](#description)
    + [Filename](#filename)
    + [Required Fields](#required-fields)
    + [Optional Fields](#optional-fields)
  * [Share your Module](#share-your-module)
    + [Prepare](#prepare)
    + [Upload](#upload)

# Description

This repository acts as a 'database' for publicly available NAP modules. Create a *pull request* following the instructions below to register your own module. All registered modules are automatically indexed and listed on [modules.nap.tech](https://modules.nap.tech)
<br>

| modules.nap.tech                                                                                                                                                                   |
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [![Netlify Status](https://api.netlify.com/api/v1/badges/90424c1c-65ad-4635-b37e-f068853dac2c/deploy-status)](https://app.netlify.com/sites/modules-nap-tech/deploys/?branch=main) |

## Register your Module

Registration of your own module is rather straight forward:

- Clone this repository
- Add a `.json` file that describes your module to `modules`
- Create a pull request and wait for validation
- The module will be listed on [modules.nap.tech](https://modules.nap.tech) after merge

The pull request is validated by the build system and reviewed by someone of the NAP team.
We accept every type of module as long as it doesn't violate our code of conduct (TODO). 

Note that you only register a description of the module, not the actual content. This gives you the freedom to  decide where you want to host your module, what license to tie to the module, how to offer the module for download etc.

### Description

Every entry in the `modules` directory must follow this `nap*.json` layout:

```
{
    "name": "napnewmodule",
    "categories":
    [
        "category_1",
        "category_2"
    ],
    "platforms":
    [
        "platform_1",
        "platform_2"
    ],
    "author":
    {
        "name": "John Doe",
        "link": "https://john-doe.com"
    },
    "description": "This module adds ... to NAP",
    "link": "https://github.com/johndoe/napnewmodule",
    "image": "https://john-doe.com/image.jpg"
}
```

You can take one of the descriptions in `/modules` as an example. 

### Filename

The filename **must** begin with `nap` otherwise it won't be indexed, for example:

```
napcamerasupport.json
```

### Required Fields

The following fields are required:

| Field         | Description                         |
|:--------------|:------------------------------------|
| name          | module name                         |
| author        | author name                         |
| description   | brief description of the module     |
| link          | download link or link to repository |


### Optional Fields

The following fields are optional:

| Field       | Description                               |
|:------------|:------------------------------------------|
| categories  | list of categories the module falls into  |
| platforms   | list of supported platforms (linux, etc.) |
| image       | additional image to be displayed          |

## Share your Module

User modules are kept in the `modules` directory under the nap root.  A typical module has the following content, which will be included when the module is prepared for sharing:

| Content                 | Directory  | Required |
|:------------------------|------------|----------|
| source code             | src        | yes      |
| thirdparty dependencies | thirdparty | no       |
| demo application        | demo       | no       |

### Prepare

Run `tools/prepare_module_to_share` with as the input argument the module you want to share, for example:
```
cd tools
./prepare_module_to_share.sh naptween
```

This prepares a **copy** of the `naptween` module that is optimized for sharing. The copy of the module is moved next to the nap root.  Add the `--help` flag for more information about the available options. 

### Upload

Upload the contents of your module to a service of your liking, for example [Github](https://github.com) or [Gitlab](https://gitlab.com). Note that the directory is already initialized as a Git repository, which makes it easier to deploy.

### Share

Share your module by following the [registration procedure](#register-your-module) above. 

