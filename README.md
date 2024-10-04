# Avataar-Project
Problem Statement: Place an object’s image in a text-conditioned scene
 Recent advancement in generative AI has led to a development of a lot of creative workflows. One
 such workflow is to use generative AI techniques for creating realistic product photographs
 (traditionally done in a studio) to display a product on e-commerce websites to appeal to users. The
 concrete problem is given an image of an object with a white background, generating a
 text-conditioned scene with the image placed naturally in the scene with the final output looking
 coherent.
 “Realism” of the scene is an open-ended challenge and the perception of realism can depend on a lot
 of factors like aspect ratio of the object relative to the scene, spatial placement of the object, lighting
 of the scene matching the object. The task is to come up with approaches to make the scene as
 natural looking as possible.
 
Overview of Logic

1. Input Handling: The code takes command-line arguments for the object image, text prompt, output image path, number of images to generate, and number of frames for the video.

2. Background Removal: It uses the rembg library to remove the background from the input object image, allowing for seamless integration into the generated scene.

3. Scene Generation: The code leverages the Stable Diffusion model to generate a scene based on the provided text prompt. This model is designed to create realistic images based on textual descriptions.

4. Segmentation: The DeepLabV3 model is used for segmenting the generated scene. This helps in identifying different regions within the image (like surfaces, backgrounds, etc.) where the object can be logically placed.

5. Object Detection: The YOLOv8 model is utilized for detecting any objects already present in the generated scene. This is essential for ensuring that the new object does not overlap or interfere with existing elements.

6. Object Scaling: The code scales the object based on the dimensions of the scene. This ensures that the object is proportionate to the scene, enhancing realism.

7. Positioning Logic: The code identifies valid positions for placing the object using the segmentation mask and the bounding boxes of detected objects. It considers factors like the type of region (e.g., a table or countertop) and ensures that the object is not placed on top of other detected objects.
If no valid positions are found, it defaults to a random position within the scene.

8. Lighting Adjustment: The object's brightness is adjusted to match the lighting conditions of the generated scene, helping to create a cohesive look.

9. Image Composition: The final image is composed by pasting the object onto the generated scene at the determined position, resulting in a natural-looking image.

10. Video Generation: If multiple images are generated, they can be compiled into a video, showcasing the object in various scenes. The frames are resized to a consistent size, and the video is saved with a specified frame rate.

Summary

The code combines various AI techniques, including background removal, image generation from text prompts, scene segmentation, and object detection, to create a coherent and visually appealing output. By ensuring that the object is logically placed within a generated scene, the code addresses the challenge of realism in product photography for e-commerce applications.
