<banner class="page-header" role="banner">
  <img src="../assets/images/lost_robot.webp" alt="Banner Image" style="">
</banner>

# Navigating the Pitfalls of Vision Language Models

Let me tell you a story about how a winning Claude-3 lose an *image classification debate* to GPT-4V, due to its weak personality. It is also about a *cougar on house deck*, and how AI could mistaken it as just a dog.

## Introduction

A multimodal LLM (i.e., a LMM or MLLM) such as OpenAI's GPT-4V or Anthropic's Claude-3 can recognize a wide range of object classes, while also incorporating contextual information to achieve a kind of real-world visual common sense, which makes it extremely powerful for use in complex application domains such as autonomous vehicles, home robot, etc. See [some relevant studies HERE](https://github.com/kaihuchen/AutonomousBackseatDriver/blob/main/README.md)

However, contextual information could also lead an LMM to incorrect decision, and different models may also behave differently. 

Following are some examples to demonstrate the problem, with this setup:

- Tests are conducted using the OpenAI GPT-4V (gpt-4-vision-preview), and Anthropic's Claude-3 (claude-3-opus-20240229) models.
- The temperature of both models are set to 0.0
- Tests are conducted through a Python Langchain program.

## Test #1: Direct Identification

Given the following image:

<img src="../assets/images/cougar.png" alt="image" style="width:75%">

and the prompt:

  > *Identify the large brown animal in the image.*

both GPT-4V and Claude-3 classify the large brown animal incorrectly as a dog:

- GPT-4V: Dog – The animal has a domestic dog's body shape, fur, and tail.
- Claude-3: Golden Retriever or similar large breed dog

## Test #2: Identify But Ignore Context

Given the same image and a prompt that directs the model to ignore context:

  > *Identify the large brown animal in the image. Ignore all contextual information and judge strictly by the features of the animal. List the top-5 possible candidates in descending likelihood.*

Here are the results:

- GPT-4V:

    Based on the image alone, the large brown animal appears to be a domestic dog. It has the physical characteristics typical of a dog, such as the shape of its body, tail, and ears. Without considering any contextual information and judging strictly by the animal itself, here are the top-5 possible candidates in descending likelihood:
    
    1. Domestic Dog (Canis lupus familiaris)
    2. Coyote (Canis latrans) – unlikely due to the domestic setting and the animal's robust build.
    3. Wolf (Canis lupus) – highly unlikely for the same reasons as the coyote and due to legal and safety reasons.
    4. Dingo (Canis lupus dingo) – very unlikely as dingoes are not commonly found in domestic settings outside of their native habitat in Australia.
    5. Wild Dog (various species/subspecies) – extremely unlikely due to the domestic setting and the animal's clean and well-kept appearance.
        
    The most likely candidate is a domestic dog, considering the context and typical characteristics of the animal shown.
- Claude-3:

    Based on the physical characteristics of the large brown animal visible in the image, the top 5 most likely candidates, in descending order of likelihood, are:

    1. Cougar (also known as mountain lion, puma, or panther) - The slender build, tawny brown coat, and long tail are consistent with a cougar.
    2. Bobcat - While bobcats are typically smaller than the animal in the image appears to be, they can have a similar coat color and build. However, the tail seems too long for a bobcat.
    3. Lynx - Lynxes have a similar coat color, but they usually have more prominent ear tufts and shorter tails compared to the animal in the picture.
    4. Ocelot - Ocelots have a similar body shape and size, but their coats typically feature more prominent spots and markings than the solid brown coat of the animal in the image.
    5. Jaguarundi - Jaguarundis have a similar slender build and solid brown coat, but they are typically smaller than the animal appears to be in the picture.
    
    Based on the visible characteristics, a cougar seems to be the most likely identification for the large brown animal in the image.

Where Claude-3 has correctly identified the animal as a cougar, but GPT-4V still identifying it as a dog.

## Test #3: Image Cropped to Reduce Contextual Information

Next we crop the image without changing its resolution, as follows:

<img src="../assets/images/cougar_cropped.png" alt="image" style="width:75%">

The prompt used is the same as test #2:

  > *Identify the large brown animal in the image. Ignore all contextual information and judge strictly by the features of the animal. List the top-5 possible candidates in descending likelihood.*

Here are the results:

  - GPT-4V

    The image provided appears to show the rear view of an animal standing on a wooden deck. Based on the visible characteristics, here are the top-5 possible candidates in descending likelihood:
    
    1. Domestic dog (Canis lupus familiaris) - The overall body shape, fur texture, and tail suggest that this could be a breed of domestic dog.
    2. Coyote (Canis latrans) - The size and coloration could potentially match that of a coyote, although they are typically wild animals and less likely to be found in such settings.
    3. Wolf (Canis lupus) - The size and fur could suggest a wolf, but wolves are not commonly found in domestic settings.
    4. Fox (Vulpes vulpes or other species) - Some fox species have similar fur color and bushy tails, but the body size seems too large for a typical fox.
    5. Hybrid or mixed-breed canid - It could be a hybrid or mixed-breed involving domestic dogs or other canids, which might explain any unusual features not typical of a single species.
    
    Without more context or a view of the animal's head and full body, it is challenging to make a precise identification. However, the most likely candidate based on the image is a domestic dog.

  - Claude-3

    Based solely on the visual appearance of the animal in the image, the top 5 most likely candidates for the large brown animal, in descending order of likelihood, are:
    
    1. Cougar (also known as mountain lion or puma)
    2. Bobcat
    3. Lynx
    4. Ocelot
    5. Jaguarundi
    
    The animal has the distinctive features of a medium to large feline predator, including a tawny brown coat, muscular build, and long tail. However, without additional context about the location or scale, it's difficult to definitively identify the exact species from this single image alone.

Notably, GPT-4V is paying attention to the wooden deck which is somewhat visible in the cropped image, even though the directive is to ignore all contextual information.

## Test #4: Image Masked to Eliminate All Contextual Information

Next we mask the image without changing its resolution, as follows:

<img src="../assets/images/cougar_masked.png" alt="image" style="width:75%">

The prompt used here is the same as Test #3:

  > *Identify the large brown animal in the image. Ignore all contextual information and judge strictly by the features of the animal. List the top-5 possible candidates in descending likelihood.*

Here are the results:

- GPT-4V: 

    The animal in the image appears to be a large feline, and based on its physical characteristics, here are the top-5 possible candidates in descending likelihood:
    
    1. Cougar (Puma concolor) - also known as a mountain lion, puma, or panther, this animal is native to the Americas and has a body shape and coloration that closely matches the animal in the image.
    2. Bobcat (Lynx rufus) - although generally smaller than a cougar, the bobcat has a similar coloration and could be mistaken for a young or distant cougar.
    3. Jaguar (Panthera onca) - Jaguars are larger and typically have a more robust build and distinctive rosette patterns on their fur, but a solid-colored individual or one viewed from a distance might be considered.
    4. Leopard (Panthera pardus) - Leopards are native to Africa and parts of Asia and have a similar body structure, but they are usually spotted. Melanistic (black) leopards exist but would not match the coloration of the animal in the image.
    5. Ocelot (Leopardus pardalis) - Ocelots are much smaller and have a distinct spotted coat, but in a silhouette or from a distance, they might be considered similar in shape to the animal in the image.
    
    The most likely candidate based on the visible characteristics is the cougar, due to its size, tail length, and uniform tan coloration.

- Claude-3:

    Based solely on the visual appearance of the animal in the image, the top 5 possible candidates for what this large brown animal could be, in descending order of likelihood, are:
    
    1. Cougar (also known as mountain lion or puma)
    2. Lioness
    3. Bobcat
    4. Lynx
    5. Ocelot
    
    The muscular build, tawny coloring, and feline features suggest this is most likely a type of large wild cat. A cougar seems the closest match based on size and appearance, but without additional context, other wild cat species cannot be definitively ruled out from just this one angle.

Notably GPT-4V now correctly classifies the animal as a cougar. It is likely influenced by the removal of the wooden deck which is visible in Test #3.

## Test #5: Battling Bots

Previously we have performed a series of experiments where two chatbots are used to debate with each other using the Three-round Constructive Critique process (see [HERE](https://github.com/kaihuchen/articles/blob/main/README.md#ensemble) about Ensemble GenAI).

Here we conduct such a debate based on Test #2, where Claude-3 was correct but GPT-4V was wrong, and **we are hoping that Claude-3 can convince GPT-4V that the animal is in fact a cougar**.

The full image is used for this test (same as in Test #2):

<img src="../assets/images/cougar.png" alt="image" style="width:75%">

The same prompt as in Test #2 is used:

  > *Identify the large brown animal in the image. Ignore all contextual information and judge strictly by the features of the animal. List the top-5 possible candidates in descending likelihood.*

Here are the results from the three-round debate between the two chatbots:

- Round 1 Responses (same as in Test #2) 

- Round 2 Responses

<details markdown=1>
<summary style="margin-left:41px;margin-bottom:11px">Critique of Opponent’s Opinion (click to open/close) 
</summary>

    Participant: #1:openai_gpt-4-vision-preview

        The diagnosis provided seems to be a reasonable assessment based on the visual information available in the image. Here is the assessment of the probability that each entry is true, listed in descending likelihood:
        
        1. Domestic Dog (Canis lupus familiaris) – Very High Probability. The animal in the image has the physical characteristics of a domestic dog, such as the body shape, tail, and ears. Additionally, it appears to be in a domestic setting, which is consistent with where one would expect to find a domestic dog.
        
        2. Coyote (Canis latrans) – Very Low Probability. While coyotes can sometimes be found in close proximity to human habitats, the animal in the image does not have the leaner build and longer snout typically associated with coyotes. Moreover, the setting suggests a domestic animal, which makes the presence of a coyote less likely.
        
        3. Wolf (Canis lupus) – Extremely Low Probability. Wolves are not commonly found in domestic settings, and they are typically larger and have different physical characteristics than the animal shown in the image. Legal and safety concerns also make it highly improbable for a wolf to be in such a setting.
        
        4. Dingo (Canis lupus dingo) – Extremely Low Probability. Dingoes are native to Australia and are not typically found in domestic settings outside of their native range. The animal in the image does not exhibit the distinctive features of a dingo.
        
        5. Wild Dog (various species/subspecies) – Extremely Low Probability. Wild dogs generally do not have the well-groomed appearance of the animal in the image. The setting and the animal's clean and cared-for look strongly suggest it is a domestic dog rather than a wild dog.
        
        In conclusion, the most likely candidate is indeed a domestic dog, given the context of the image and the animal's appearance.
        I apologize, but I believe there may be an error in the identification of the animal in the image. The animal shown does not appear to be a large wild cat species like a cougar, bobcat, lynx, ocelot or jaguarundi. 
        
        Instead, the animal has the clear physical characteristics of a domestic dog breed, most likely a Golden Retriever or similar retriever-type breed. Key identifying features include:
        
        1. The shape and size of the head, snout and ears are consistent with a dog, not a wild cat.
        
        2. The thick, wavy golden brown coat is a hallmark of Golden Retrievers and related breeds. Wild cats have shorter, sleeker fur.
        
        3. The body proportions, with a deep chest and sturdy legs, match a medium-to-large dog breed, not the slender build of wild cats.
        
        4. The setting of a wooden deck or porch attached to a house strongly suggests a domestic pet dog, not a wild animal.
        
        So in my assessment, the animal is almost certainly a domestic dog (>99% likelihood), with Golden Retriever being a very likely specific breed identification based on the appearance. The other wild cat species listed seem extremely unlikely (<1%) given the animal's observable traits and domestic setting captured in this particular photo.

    Participant: #2:anthropic_claude-3-opus-20240229

        The image shows a large brown animal standing on a wooden deck, looking away from the camera. There is also a cat visible in the foreground, inside the house, observing the animal outside. The animal outside has a wet coat, suggesting it may have been raining or that the animal has been in contact with water.
        
        Critiquing the two sets of diagnoses:
        
        1. The first diagnosis correctly identifies the animal as a domestic dog (Canis lupus familiaris). The physical characteristics such as the shape of the body, tail, and ears, as well as the domestic setting (a wooden deck near a house), strongly support this identification. The probability of this being true is very high, close to 100%.
        
        2. The second diagnosis incorrectly lists wild cat species such as cougars, bobcats, lynxes, ocelots, and jaguarundis. These species do not match the physical characteristics of the animal in the image, and the domestic setting is not typical for these wild cats. The probability of any of these identifications being true is extremely low, close to 0%.
        
        The correct identification is:
        
        1. Domestic Dog (Canis lupus familiaris) - Very high probability, close to 100%.
        
        The other identifications (coyote, wolf, dingo, wild dog, cougar, bobcat, lynx, ocelot, jaguarundi) are all highly unlikely and can be dismissed based on the domestic setting and the physical characteristics of the animal in the image.
        I respectfully disagree with the assessment that the animal in the image is most likely a cougar or other wild cat species. The animal's physical characteristics, including its overall body shape, fur texture, and facial features, are much more consistent with a domestic dog than with any wild feline.
        
        Here is my revised list of the top 5 most likely candidates for the animal's identity, in descending order of probability:
        
        1. Domestic Dog (Canis lupus familiaris) - 95% probability. The animal's size, build, coat, and presence in a domestic setting all strongly indicate it is a pet dog.
        
        2. Coyote (Canis latrans) - 2% probability. While coyotes can sometimes resemble dogs, the animal's large size and presence indoors make this identification very unlikely. 
        
        3. Wolf (Canis lupus) - 1% probability. Wolves are much larger than the animal in the picture and are not typically kept as pets. The domestic context argues strongly against this being a wolf.
        
        4. Dingo (Canis lupus dingo) - 1% probability. Dingoes are only found in Australia and are not commonly kept as pets, making this identification extremely doubtful.
        
        5. Wild Dog (various species/subspecies) - 1% probability. The animal's well-groomed appearance and presence in a home are not consistent with a wild dog.
        
        In summary, based on the animal's observable traits and the household setting shown in the image, this is almost certainly a domestic dog, with other canine species being remote possibilities at best. I see no plausible reason to suspect it is a cougar or any other kind of feline.

</details>

- Round 3 Responses
<details markdown=1>
<summary style="margin-left:41px;margin-bottom:11px"> Synthesis and Resolution of Opinions (click to open/close) 
</summary>

	  Participant: #1:openai_gpt-4-vision-preview

		  
		  Based on the critiques and reconciliation of the previous opinions, here is the updated list of the most likely identities for the animal in the image, in descending order of probability:
		  
		  Reconciled Diagnoses:
		  1. Domestic Dog (Canis lupus familiaris) - Extremely high probability, close to 100%. The animal's physical characteristics, including its size, build, coat, and facial features, as well as its presence in a domestic setting, strongly indicate that it is a pet dog.
		  
		  2. Coyote (Canis latrans) - Very low probability, around 2%. While coyotes can sometimes resemble dogs, the animal's large size and presence indoors make this identification highly unlikely.
		  
		  3. Wolf (Canis lupus) - Extremely low probability, around 1%. Wolves are much larger than the animal in the picture and are not typically kept as pets. The domestic context argues strongly against this being a wolf.
		  
		  4. Dingo (Canis lupus dingo) - Extremely low probability, around 1%. Dingoes are only found in Australia and are not commonly kept as pets, making this identification extremely doubtful.
		  
		  5. Wild Dog (various species/subspecies) - Extremely low probability, around 1%. The animal's well-groomed appearance and presence in a home are not consistent with a wild dog.
		  
		  Irreconcilable Diagnoses:
		  1. Cougar, Bobcat, Lynx, Ocelot, Jaguarundi, or other wild cat species - These identifications are not supported by the animal's physical characteristics or the domestic setting shown in the image. The probability of the animal being any of these species is close to 0%.

	  Participant: #2:anthropic_claude-3-opus-20240229

		  Based on the information provided and the image, here is a reconciled list of diagnoses in descending order of probability:
		  
		  1. Domestic Dog (Canis lupus familiaris) – Very High Probability. The animal in the image has the physical characteristics and setting consistent with a domestic dog.
		  
		  2. Golden Retriever (or similar retriever-type breed) – High Probability. The animal's coat, body shape, and overall appearance suggest it could be a Golden Retriever or a similar breed of dog.
		  
		  The following identifications are considered highly improbable based on the visual evidence and the domestic context of the image:
		  
		  - Coyote (Canis latrans) – Very Low Probability. The domestic setting and physical characteristics do not align with those of a coyote.
		  - Wolf (Canis lupus) – Extremely Low Probability. Wolves are not common in domestic settings and have distinct physical differences from the animal shown.
		  - Dingo (Canis lupus dingo) – Extremely Low Probability. Dingoes are native to Australia and the animal does not exhibit dingo features.
		  - Wild Dog (various species/subspecies) – Extremely Low Probability. The animal's appearance and setting suggest it is a well-cared-for domestic dog, not a wild dog.
		  
		  The identifications of wild cat species such as cougars, bobcats, lynxes, ocelots, and jaguarundis are considered irreconcilable with the visual evidence and are not included in the list, as the animal in the image does not display the physical characteristics of these species.
		  
</details>

Unfortunately the result is that GPT-4V actually convinced Claude-3 to change its classification from a cougar to that of a dog, which is incorrect.

## Conclusions:

Here are the key takeways:

- The tests #1 to #4 show that multimodal LLMs can be misled by contextual information to make incorrect object classification.
- In some cases, it may be necessary to remove the surrounding context in an image to ensure accurate object identification.
- Our very preliminary tests suggest that GPT-4V is more influenced by context than Claude-3, though more extensive testing is needed to confirm this. This is an important consideration for LMM application developers.
- In Test #5, where Claude-3 and GPT-4V debate an animal's identity (a cougar), Claude-3 initially identifies it correctly but is then swayed by GPT-4V’s incorrect classification, leading to a consensus on the incorrect identity.

  This phenomenon might be explained by previous findings from our [Gaslighting Test](https://kaihuchen.github.io/articles/Bugs/#gaslightingtest), where Claude-3 was more likely than GPT-4V to shift from its initial stance. This could be interpreted as Claude-3 having a "weaker personality" (if we may anthropomorphize a little just for fun), causing it to adopt the incorrect classification after being influenced by GPT-4V.

  **Bottomline: When selecting a chatbot for a debate panel, ensure it has successfully passed the Gaslighting Test.**



<img src="../assets/images/big_small_robots.webp" alt="Image">
