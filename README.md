# custom-docs-template

> [!IMPORTANT]  
> this is just a test for custom quarto theme/format as an extension
> 
> Credits: based on [posit-dev/product-doc-theme](https://github.com/posit-dev/product-doc-theme)

Shared theme for Custom product documentation

## How to iniate a quarto extenstion

Excecute this command and follow the instructions to create a [custom format](https://quarto.org/docs/extensions/formats.html#quick-start)

```bash
quarto create extension format:html
```

## Usage

First, install the extension:

```bash
quarto add khammami/custom-docs-template@v{version}
```

Next, update your project type and format in `_quarto.yml`:

```yaml
project:
  title: "Custom Documentation"
  type: custom-docs
```

### Additional configuration entries

The following entries may be unique to each product. Please review the following and make manual updates to your project, as required.

#### Navbar

If you have `website.navbar.right` entries in your `_quarto.yml`,
merge the following with the existing entries:

```yaml
website:
  navbar:
    right:
      - icon: "list"
        menu:
          - text: "docs.custom.co"
            href: "https://docs.custom.co"
          - text: "Custom Support"
            href: "https://support.custom.co/hc/en-us/"
```

#### Footer

Use the following `website.page-footer` in your `_quarto.yml`:

```yaml
website:
  page-footer:
    left: |
      Copyright &copy; 2000-{{< env CURRENT_YEAR >}} Custom Software, PBC. All Rights Reserved.
    center: |
      Custom PRODUCT {{< env PRODUCT_VERSION >}}
    right:
      - icon: question-circle-fill
        aria-label: 'Link to Custom Support'
        href: "https://support.custom.co/hc/en-us"
      - icon: lightbulb-fill
        aria-label: 'Link to Custom Solutions'
        href: "https://solutions.custom.co/"
      - text: "<img alt='Link to Custom Documentation' src='/_extensions/custom-docs/assets/images/custom-guide-ltmd.svg' id='footer-right-logo'>"
        href: "https://docs.custom.co/"
      - text: "<img alt='Link to main Custom site' src='/_extensions/custom-docs/assets/images/custom-icon-fullcolor.svg' id='footer-right-custom-logo'>"
        href: "https://custom.co/"
```

Make the following modifications:

- **Copyright:** Copyright dates are represented as a range from the year of
  first product release until now. Adapt the example for your product and
  how that information is made available.

- **Product name:** Replace the `PRODUCT` placeholder with the product name.

- **Product version:** Adapt the version for your product based on how that
  information is made available.

- **Images:** Copy the two images from the extension into your project and update the `src` paths.

  For example, you may have a top-level `images` directory:

  ```bash
  cp _extensions/custom-dev/custom-docs/assets/images/custom-guide-ltmd.svg images
  cp _extensions/custom-dev/custom-docs/assets/images/custom-icon-fullcolor.svg images
  ```

  These images are also available [from
  GitHub](https://github.com/khammami/custom-docs-template/tree/main/_extensions/custom-docs/assets/images).

By copy/pasting and editing these entries into your project's yml, those entries will overwrite 1:1 entries in the `_extension.yml`.

## Development

If you are modifying this extension, use Quarto to preview your changes
against the sample project defined here.

```bash
quarto preview
```

### Release

To release a new version of this theme:

1. Make sure that the extension declares the target version and documents its
    changes.

    1. Update
        [`README.md`](https://github.com/custom-dev/product-doc-theme/blob/main/README.md);
        installation instructions reference the latest release version.
    1. Update
        [`_extensions/custom-docs/_extension.yml`](https://github.com/custom-dev/product-doc-theme/blob/main/_extensions/custom-docs/_extension.yml);
        the extension declares its version.
    1. Update
        [`changelog.md`](https://github.com/custom-dev/product-doc-theme/blob/main/changelog.md);
        make sure recent changes are announced.

    Commit and merge both changes to `main`.

2. Tag the target commit and push the tag.

    ```bash
    git tag -a v1.1.0 -m 'Release 1.1.0'
    git push origin v1.1.0
    ```

3. Create a GitHub release from [that tag](https://github.com/custom-dev/product-doc-theme/tags).
