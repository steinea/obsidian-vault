# Glaze

[[tools]]

<https://glaze.cs.uchicago.edu/>

> Generative AI models have changed the way we create and consume content, particularly images and art. Diffusion models such as MidJourney and Stable Diffusion have been trained on large datasets of scraped images from online, many of which are copyrighted, private, or sensitive in subject matter. Many artists have discovered significant numbers of their art pieces in training data such as LAION-5B, without their knowledge, consent, credit or compensation.
>
> To make it worse, many of these models are now used to copy individual artists, through a process called style mimicry. Home users can take art work from human artists, perform "fine-tuning" or LoRA on models like stable diffusion, and end up with a model that is capable of producing arbitrary images in the "style" of the target artist, when evoked with their name as a prompt. Popular independent artists find low quality facsimilies of their artwork online, often with their names still embedded in the metadata from model prompts.
>
> Style mimicry produces a number of harmful outcomes that may not be obvious at first glance. For artists whose styles are intentionally copied, not only do they see loss in commissions and basic income, but low quality synthetic copies scattered online dilute their brand and reputation. Most importantly, artists associate their styles with their very identity. Seeing the artistic style they worked years to develop taken to create content without their consent or compensation is akin to identity theft. Finally, style mimicry and its impacts on successful artists have demoralized and disincentivized young aspiring artists. We have heard administrators at art schools and art teachers talking about plummeting student enrollment, and panicked parents concerned for the future of their aspiring artist children.
>
> _**Glaze**_ is a system designed to protect human artists by disrupting style mimicry. At a high level, Glaze works by understanding the AI models that are training on human art, and using machine learning algorithms, computing a set of minimal changes to artworks, such that it appears unchanged to human eyes, but appears to AI models like a dramatically different art style. For example, human eyes might find a _glazed_ charcoal portrait with a realism style to be unchanged, but an AI model might see the glazed version as a modern abstract style, a la Jackson Pollock. So when someone then prompts the model to generate art mimicking the charcoal artist, they will get something quite different from what they expected.

Related tool: [[Nightshade]]