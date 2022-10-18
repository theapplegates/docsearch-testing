---
title: Page 3
description: Lorem ipsum dolor sit amet - 3
layout: ../../layouts/MainLayout.astro
---

This is a fully-featured page, written in Markdown!

## Section A

Lorem ipsum dolor sit amet, **consectetur adipiscing elit**. Sed ut tortor _suscipit_, posuere ante id, vulputate urna. Pellentesque molestie aliquam dui sagittis aliquet. Sed sed felis convallis, lacinia lorem sit amet, fermentum ex. Etiam hendrerit mauris at elementum egestas. Vivamus id gravida ante. Praesent consectetur fermentum turpis, quis blandit tortor feugiat in. Aliquam erat volutpat. In elementum purus et tristique ornare. Suspendisse sollicitudin dignissim est a ultrices. Pellentesque sed ipsum finibus, condimentum metus eget, sagittis elit. Sed id lorem justo. Vivamus in sem ac mi molestie ornare.

## Section B

Nam quam dolor, pellentesque sed odio euismod, feugiat tempus tellus. Quisque arcu velit, ultricies in faucibus sed, ultrices ac enim. Nunc eget dictum est. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam ex nisi, egestas mollis ultricies ut, laoreet suscipit libero. Nam condimentum molestie turpis. Sed vestibulum sagittis congue. Maecenas tristique enim et tincidunt tempor. Curabitur ac scelerisque nulla, in malesuada libero. Praesent eu tempus odio. Pellentesque aliquam ullamcorper quam at gravida. Sed non fringilla mauris. Aenean sit amet ultrices erat. Vestibulum congue venenatis tortor, nec suscipit tortor. Aenean pellentesque mauris eget tortor tincidunt pharetra.

## Section C

```markdown
---
title: Markdown Page!
lang: en
layout: ~/layouts/MainLayout.astro
---

# Markdown example

This is a fully-featured page, written in Markdown!

## Section A

Lorem ipsum dolor sit amet, **consectetur adipiscing elit**. Sed ut tortor _suscipit_, posuere ante id, vulputate urna. Pellentesque molestie aliquam dui sagittis aliquet. Sed sed felis convallis, lacinia lorem sit amet, fermentum ex. Etiam hendrerit mauris at elementum egestas. Vivamus id gravida ante. Praesent consectetur fermentum turpis, quis blandit tortor feugiat in. Aliquam erat volutpat. In elementum purus et tristique ornare. Suspendisse sollicitudin dignissim est a ultrices. Pellentesque sed ipsum finibus, condimentum metus eget, sagittis elit. Sed id lorem justo. Vivamus in sem ac mi molestie ornare.

## Section B

@astrojs/image
v0.10.0 GitHub npm
⚠️ This integration is still experimental! Only node environments are supported currently, stay tuned for Deno support in the future!

This Astro integration makes it easy to optimize images in your Astro project, with full support for SSG builds and server-side rendering!

Images play a big role in overall site performance and usability. Serving properly sized images makes all the difference but is often tricky to automate.

This integration provides <Image /> and <Picture> components as well as a basic image transformer, with full support for static sites and server-side rendering. The built-in image transformer is also replaceable, opening the door for future integrations that work with your favorite hosted image service.

The astro add command-line tool automates the installation for you. Run one of the following commands in a new terminal window. (If you aren’t sure which package manager you’re using, run the first command.) Then, follow the prompts, and type “y” in the terminal (meaning “yes”) for each one.

# Using NPM
npx astro add image
# Using Yarn
yarn astro add image
# Using PNPM
pnpm astro add image
If you run into any issues, feel free to report them to us on GitHub and try the manual installation steps below.

First, install the @astrojs/image package using your package manager. If you’re using npm or aren’t sure, run this in the terminal:

npm install @astrojs/image
Then, apply this integration to your astro.config.* file using the integrations property:

astro.config.mjs
import image from '@astrojs/image';

export default {
  // ...
  integrations: [image()],
}
Installing sharp (optional)

The default image transformer is based on Squoosh and uses web assembly libraries to support most deployment environments.

If you are building a static site or using an SSR deployment host that supports NodeJS, we recommend installing sharp for faster builds and more fine-grained control of image transformations.

First, install the sharp package using your package manger. If you’re using npm or aren’t sure, run this in the terminal:

npm install sharp
Then, update the integration in you astro.config.* file to use the built-in sharp image transformer.

astro.config.mjs
---
import image from '@astrojs/image';

export default {
  // ...
  integrations: [image({
	serviceEntryPoint: '@astrojs/image/sharp'
  })],
}
---
For the best development experience, add the integrations type definitions to your project’s env.d.ts file.

// Replace `astro/client` with `@astrojs/image/client`
/// <reference types="@astrojs/image/client" />
Or, alternatively if your project is using the types through a tsconfig.json

{
  "compilerOptions": {
	// Replace `astro/client` with `@astrojs/image/client`
	"types": ["@astrojs/image/client"]
  }
}
src/pages/index.astro
---
import { Image, Picture } from '@astrojs/image/components';
---
The included image transformers support resizing images and encoding them to different image formats. Third-party image services will be able to add support for custom transformations as well (ex: blur, filter, rotate, etc).

Astro’s <Image /> and <Picture /> components require the alt attribute, which provides descriptive text for images. A warning will be logged if alt text is missing, and a future release of the integration will throw an error if no alt text is provided.

If the image is merely decorative (i.e. doesn’t contribute to the understanding of the page), set alt="" so that the image is properly understood and ignored by screen readers.

The built-in <Image /> component is used to create an optimized <img /> for both remote images hosted on other domains as well as local images imported from your project’s src directory.

In addition to the component-specific properties, any valid HTML attribute for the <img /> included in the <Image /> component will be included in the built <img />.

Type: string | ImageMetadata | Promise<ImageMetadata>
Required: true

Source for the original image file.

For images located in your project’s src: use the file path relative to the src directory. (e.g. src="../assets/source-pic.png")

For images located in your public directory: use the URL path relative to the public directory. (e.g. src="/images/public-image.jpg")

For remote images, provide the full URL. (e.g. src="https://astro.build/assets/blog/astro-1-release-update.avif")

Type: string
Required: true

Defines an alternative text description of the image.

Set to an empty string (alt="") if the image is not a key part of the content (e.g. it’s decoration or a tracking pixel).

Type: 'avif' | 'jpeg' | 'png' | 'webp'
Default: undefined

The output format to be used in the optimized image. The original image format will be used if format is not provided.

Type: number
Default: undefined

The compression quality used during optimization. The image service will use a default quality if not provided.

Type: number
Default: undefined

The desired width of the output image. Combine with height to crop the image to an exact size, or aspectRatio to automatically calculate and crop the height.

Dimensions are optional for local images, the original image size will be used if not provided.

For remote images, the integration needs to be able to calculate dimensions for the optimized image. This can be done by providing width and height or by providing one dimension and an aspectRatio.

Type: number
Default: undefined

The desired height of the output image. Combine with width to crop the image to an exact size, or aspectRatio to automatically calculate and crop the width.

Dimensions are optional for local images, the original image size will be used if not provided.

For remote images, the integration needs to be able to calculate dimensions for the optimized image. This can be done by providing width and height or by providing one dimension and an aspectRatio.

Type: number | string
Default: undefined

The desired aspect ratio of the output image. Combine with either width or height to automatically calculate and crop the other dimension.

A string can be provided in the form of {width}:{height}, ex: 16:9 or 3:4.

A number can also be provided, useful when the aspect ratio is calculated at build time. This can be an inline number such as 1.777 or inlined as a JSX expression like aspectRatio={16/9}.

Type: ColorDefinition
Default: undefined

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

The background color is used to fill the remaining background when using contain for the fit property.

The background color is also used for replacing the alpha channel with sharp’s flatten method. In case the output format doesn’t support transparency (i.e. jpeg), it’s advisable to include a background color, otherwise black will be used as default replacement for transparent pixels.

The parameter accepts a string as value.

The parameter can be a named HTML color, a hexadecimal color representation with 3 or 6 hexadecimal characters in the form #123[abc], an RGB definition in the form rgb(100,100,100), an RGBA definition in the form rgba(100,100,100, 0.5).

Type: 'cover' | 'contain' | 'fill' | 'inside' | 'outside'
Default: 'cover'

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

How the image should be resized to fit both height and width.

Type: 'top' | 'right top' | 'right' | 'right bottom' | 'bottom' | 'left bottom' | 'left' | 'left top' | 'north' | 'northeast' | 'east' | 'southeast' | 'south' | 'southwest' | 'west' | 'northwest' | 'center' | 'centre' | 'cover' | 'entropy' | 'attention'
Default: 'centre'

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

Position of the crop when fit is cover or contain.

Type: string | ImageMetadata | Promise<ImageMetadata>
Required: true

Source for the original image file.

For images located in your project’s src: use the file path relative to the src directory. (e.g. src="../assets/source-pic.png")

For images located in your public directory: use the URL path relative to the public directory. (e.g. src="/images/public-image.jpg")

For remote images, provide the full URL. (e.g. src="https://astro.build/assets/blog/astro-1-release-update.avif")

Type: string
Required: true

Defines an alternative text description of the image.

Set to an empty string (alt="") if the image is not a key part of the content (e.g. it’s decoration or a tracking pixel).

Type: string
Required: true

The HTMLImageElement property sizes allows you to specify the layout width of the image for each of a list of media conditions.

See MDN for more details.

Type: number[]
Required: true

The list of sizes that should be built for responsive images. This is combined with aspectRatio to calculate the final dimensions of each built image.

// Builds three images: 400x400, 800x800, and 1200x1200
<Picture src={...} widths={[400, 800, 1200]} aspectRatio="1:1" />
Type: number | string
Default: undefined

The desired aspect ratio of the output image. This is combined with widths to calculate the final dimensions of each built image.

A string can be provided in the form of {width}:{height}, ex: 16:9 or 3:4.

A number can also be provided, useful when the aspect ratio is calculated at build time. This can be an inline number such as 1.777 or inlined as a JSX expression like aspectRatio={16/9}.

Type: Array<'avif' | 'jpeg' | 'png' | 'webp'>
Default: undefined

The output formats to be used in the optimized image. If not provided, webp and avif will be used in addition to the original image format.

Type: ColorDefinition
Default: undefined

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

The background color to use for replacing the alpha channel with sharp’s flatten method. In case the output format doesn’t support transparency (i.e. jpeg), it’s advisable to include a background color, otherwise black will be used as default replacement for transparent pixels.

The parameter accepts a string as value.

The parameter can be a named HTML color, a hexadecimal color representation with 3 or 6 hexadecimal characters in the form #123[abc], or an RGB definition in the form rgb(100,100,100).

Type: 'cover' | 'contain' | 'fill' | 'inside' | 'outside'
Default: 'cover'

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

How the image should be resized to fit both height and width.

Type: 'top' | 'right top' | 'right' | 'right bottom' | 'bottom' | 'left bottom' | 'left' | 'left top' | 'north' | 'northeast' | 'east' | 'southeast' | 'south' | 'southwest' | 'west' | 'northwest' | 'center' | 'centre' | 'cover' | 'entropy' | 'attention'
Default: 'centre'

This is not supported by the default Squoosh service. See the installation section for details on using the sharp service instead.

Position of the crop when fit is cover or contain.

This is the helper function used by the <Image /> component to build <img /> attributes for the transformed image. This helper can be used directly for more complex use cases that aren’t currently supported by the <Image /> component.

This helper takes in an object with the same properties as the <Image /> component and returns an object with attributes that should be included on the final <img /> element.

This can be helpful if you need to add preload links to a page’s <head>.

---
import { getImage } from '@astrojs/image';

const { src } = await getImage({src: '../assets/hero.png'});
---

<html>
  <head>
	<link rel="preload" as="image" href={src} alt="alt text">
  </head>
</html>
This is the helper function used by the <Picture /> component to build multiple sizes and formats for responsive images. This helper can be used directly for more complex use cases that aren’t currently supported by the <Picture /> component.

This helper takes in an object with the same properties as the <Picture /> component and returns an object attributes that should be included on the final <img /> element and a list of sources that should be used to render all <source>s for the <picture> element.

The integration can be configured to run with a different image service, either a hosted image service or a full image transformer that runs locally in your build or SSR deployment.

During development, local images may not have been published yet and would not be available to hosted image services. Local images will always use the built-in image service when using astro dev.

The serviceEntryPoint should resolve to the image service installed from NPM. The default entry point is @astrojs/image/squoosh, which resolves to the entry point exported from this integration’s package.json.

astro.config.mjs
import image from '@astrojs/image';

export default {
  integrations: [image({
	// Example: The entrypoint for a third-party image service installed from NPM
	serviceEntryPoint: 'my-image-service/astro.js'
  })],
}
The logLevel controls can be used to control how much detail is logged by the integration during builds. This may be useful to track down a specific image or transformation that is taking a long time to build.

astro.config.mjs
import image from '@astrojs/image';

export default {
  integrations: [image({
	// supported levels: 'debug' | 'info' | 'warn' | 'error' | 'silent'
	// default: 'info'
	logLevel: 'debug'
  })],
}
During static builds, the integration will cache transformed images to avoid rebuilding the same image for every build. This can be particularly helpful if you are using a hosting service that allows you to cache build assets for future deployments.

Local images will be cached for 1 year and invalidated when the original image file is changed. Remote images will be cached based on the fetch() response’s cache headers, similar to how a CDN would manage the cache.

By default, transformed images will be cached to ./node_modules/.astro/image. This can be configured in the integration’s config options.

export default defineConfig({
  integrations: [image({
	// may be useful if your hosting provider allows caching between CI builds
	cacheDir: "./.cache/image"
  })]
});
Caching can also be disabled by using cacheDir: false.

Image files in your project’s src directory can be imported in frontmatter and passed directly to the <Image /> component. All other properties are optional and will default to the original image file’s properties if not provided.

---
import { Image } from '@astrojs/image/components';
import heroImage from '../assets/hero.png';
---

// optimized image, keeping the original width, height, and image format
<Image src={heroImage} alt="descriptive text" />

// height will be recalculated to match the original aspect ratio
<Image src={heroImage} width={300} alt="descriptive text" />

// cropping to a specific width and height
<Image src={heroImage} width={300} height={600} alt="descriptive text" />

// cropping to a specific aspect ratio and converting to an avif format
<Image src={heroImage} aspectRatio="16:9" format="avif" alt="descriptive text" />

// image imports can also be inlined directly
<Image src={import('../assets/hero.png')} alt="descriptive text" />
Files in the /public directory are always served or copied as-is, with no processing. We recommend that local images are always kept in src/ so that Astro can transform, optimize and bundle them. But if you absolutely must keep an image in public/, use its relative URL path as the image’s src= attribute. It will be treated as a remote image, which requires an aspectRatio attribute.

Alternatively, you can import an image from your public/ directory in your frontmatter and use a variable in your src= attribute. You cannot, however, import this directly inside the component as its src value.

For example, use an image located at public/social.png in either static or SSR builds like so:

src/pages/page.astro
---
import { Image } from '@astrojs/image/components';
import socialImage from '/social.png';
---
// In static builds: the image will be built and optimized to `/dist`.
// In SSR builds: the image will be optimized by the server when requested by a browser.
<Image src={socialImage} width={1280} aspectRatio="16:9" alt="descriptive text" />
Remote images can be transformed with the <Image /> component. The <Image /> component needs to know the final dimensions for the <img /> element to avoid content layout shifts. For remote images, this means you must either provide width and height, or one of the dimensions plus the required aspectRatio.

---
import { Image } from '@astrojs/image/components';

const imageUrl = 'https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png';
---

// cropping to a specific width and height
<Image src={imageUrl} width={544} height={184} alt="descriptive text" />

// height will be recalculated to match the aspect ratio
<Image src={imageUrl} width={300} aspectRatio={16/9} alt="descriptive text" />

// cropping to a specific height and aspect ratio and converting to an avif format
<Image src={imageUrl} height={200} aspectRatio="16:9" format="avif" alt="descriptive text" />
The <Picture /> component can be used to automatically build a <picture> with multiple sizes and formats. Check out MDN for a deep dive into responsive images and art direction.

By default, the picture will include formats for avif and webp in addition to the image’s original format.

For remote images, an aspectRatio is required to ensure the correct height can be calculated at build time.

---
import { Picture } from '@astrojs/image/components';
import hero from '../assets/hero.png';

const imageUrl = 'https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png';
---

// Local image with multiple sizes
<Picture src={hero} widths={[200, 400, 800]} sizes="(max-width: 800px) 100vw, 800px" alt="descriptive text" />

// Remote image (aspect ratio is required)
<Picture src={imageUrl} widths={[200, 400, 800]} aspectRatio="4:3" sizes="(max-width: 800px) 100vw, 800px" alt="descriptive text" />

// Inlined imports are supported
<Picture src={import("../assets/hero.png")} widths={[200, 400, 800]} sizes="(max-width: 800px) 100vw, 800px" alt="descriptive text" />
If your installation doesn’t seem to be working, try restarting the dev server.
If you edit and save a file and don’t see your site update accordingly, try refreshing the page.
If refreshing the page doesn’t update your preview, or if a new installation doesn’t seem to be working, then restart the dev server.
For help, check out the #support channel on Discord. Our friendly Support Squad members are here to help!

You can also check our Astro Integration Documentation for more on integrations.

This package is maintained by Astro’s Core team. You’re welcome to submit an issue or PR!

See CHANGELOG.md for a history of changes to this integration.

More Integrations

Nam quam dolor, pellentesque sed odio euismod, feugiat tempus tellus. Quisque arcu velit, ultricies in faucibus sed, ultrices ac enim. Nunc eget dictum est. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam ex nisi, egestas mollis ultricies ut, laoreet suscipit libero. Nam condimentum molestie turpis. Sed vestibulum sagittis congue. Maecenas tristique enim et tincidunt tempor. Curabitur ac scelerisque nulla, in malesuada libero. Praesent eu tempus odio. Pellentesque aliquam ullamcorper quam at gravida. Sed non fringilla mauris. Aenean sit amet ultrices erat. Vestibulum congue venenatis tortor, nec suscipit tortor. Aenean pellentesque mauris eget tortor tincidunt pharetra.
```
