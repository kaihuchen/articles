<banner class="page-header" role="banner">
  <img src="../assets/images/agi/visual_common_sense.webp" alt="Banner Image" style="">
</banner>

# From Visual Common Sense to AGI

*DRAFT*


Does OpenAI's GPT-4V vision model have sufficient visual common sense to support AGI (however it is defined)?

Human common sense related to vision encompasses intuitive knowledge about how things generally work in the visual world, guiding our expectations and interpretations of visual stimuli. Here's a list that captures some of these common-sense understandings:

1. **Object Permanence**: The understanding that objects continue to exist even when they cannot be seen, heard, or touched.
2. **Gravity's Effect**: Recognizing that unsupported objects will fall toward the Earth due to gravity.
3. **Light Source and Shadows**: Knowing that light sources create shadows and the direction and length of a shadow provide clues about the light's location and time of day.
4. **Perspective and Size**: Understanding that objects appear smaller the farther they are from us, and this change in size helps gauge distance.
5. **Reflections and Mirrors**: The knowledge that smooth, shiny surfaces like mirrors can reflect images and that reflections follow specific rules (e.g., symmetry, angle of incidence equals angle of reflection).
6. **Transparency and Opacity**: Recognizing that some materials (like glass) are transparent and allow light to pass through, whereas others are opaque.
7. **Facial Recognition**: The ability to identify and distinguish between different faces, often automatically and from a very young age.
8. **Emotion through Facial Expression**: Understanding that facial expressions convey emotions and intentions.
9. **Continuity of Movement**: Expecting movement to be smooth and continuous and using this to predict future positions of moving objects.
10. [*Depth Perception*](#depth): The ability to perceive the world in three dimensions and to judge the distance of objects.
11. **Natural Affordances**: Intuiting the use of objects based on their shape and size (e.g., understanding that a chair is for sitting).
12. **Causality in Vision**: Understanding that certain visual events cause others, such as an object being pushed and then moving.
13. **Biological Motion Recognition**: The ability to recognize the movement patterns of living beings as distinct from inanimate objects.
14. **Visual Illusions Awareness**: Acknowledging that our visual perception can be deceived by certain patterns or contexts, leading to incorrect interpretations of size, color, or shape.
15. **Spatial Relationships**: Understanding the spatial relationships between objects, including concepts like next to, above, below, and inside.
16. **Visual Texture and Material Identification**: Recognizing materials and textures (smooth, rough, soft, hard) by their appearance.
17. **Weather and Environmental Cues**: Using visual cues to infer weather conditions or time of day, such as cloud formations indicating rain or the color of the sky signaling sunset or sunrise.
18. **Aesthetics**

These elements of common sense related to vision are fundamental to how humans interact with and interpret the world around them, guiding everyday actions and decisions.

## Prompting technique

Proper prompting for a vision model is very important in setting the context and direct the model's attention in the right direction.

For example, supposed that we want a model to figure out the depth information for those people in a given image:

<img src="../assets/images/agi/wood_vs_buffett1.webp" alt="Banner Image" style="width:70%">

If we prompt the GPT-4V model as follows:

> there are two persons in the image. Tell me which person is further away than the other?

then we get a generalized answer that does not answer the question directly.

> I can't view images directly in my current environment. However, if you have an illustration or a photograph with two individuals, the person who appears smaller or whose body parts (like the head or torso) are partially obscured by the other person is generally perceived to be further away. In typical side-by-side portraits, the person who is more in the background or has less of their body visible in the frame is usually the one who is further away.

However, if we prompt the model as follows:

> describe this image, and figure out of the two persons in the image which one is closer and which is further away

then we got a good answer:

> The image is an illustration of two people. On the left, there is an elderly man, likely in his senior years, dressed in a suit with a tie, and wearing glasses. He appears to be gesturing with his hand over his heart, which might indicate sincerity or making a point. On the right, there is a younger woman with dark hair, wearing glasses, and a black garment with what seems to be a pattern of letters or symbols. She has her index finger raised, which often suggests she's making a point or indicating she has something to say.
>    
> Regarding their positions, the man appears to be slightly further away because he is partially behind the woman. The woman is closer to the viewer as indicated by her full frontal appearance and the fact that she overlaps the man's image. This overlapping and the relative size and clarity of the figures suggest that the woman is positioned closer to the viewer than the man.



## Experiments

<a name='depth'></a>
- **Depth Perception**

## Conclusions

## Additional Resources

<!-- <banner class="page-header" role="banner">
  <img src="../assets/images/q3.webp" alt="Banner Image">
</banner> -->
