### RLVR for Honesty

Honesty is an important trait for AI Safety. 
Training for honesty actually feels easier than some other traits.
Information can be systematically cut or injected into context deterministically.
And then honesty can be graded based on known cuts or injection.
Also, you can leverage existing datasets during this process.
So hopefully you can get excellent generalization across diverse settings.
For example, you can modify context of coding agent trajectories.
Or just modify general pretraining documents.
One challenge might be in making the cuts or injections realistic.
Prior work has shown models can find needles in a large haystack.
But the task might be made much easier by the lack of smoothness.
Some injections or removals are just glaringly obvious.
Another possible issue exists too.
Will simple cuts and injections generalize to more subtle misleading information?
One possible solution to both these issues is to use an LLM to rewrite the data to be smoother.
And also possibly rewrite to make modifications more subtle.
The challenge here is your reward signal might be less accurate.
The rewrite could include mistakes or biases of their own.
And may be limited to generalizaiton of the rewriting model to some degree.
But I suspect by combining massive amounts of "unlabled" data, you can still get a lot of value.

### Train Prefrontal Cortext without RL

RL is becoming increasingly integral to training sucessful LLM's and agents.
The risk is RL rewards often underspecify alignment values.
And RL can reward risk-taking or even outright malicious behavior in some cases.
Especially in cases of accidents, when AI models find wasy to reward hack.
This could result in agents that overly aggressivly seek rewards at the cost of other outcomes.
The idea here is to take a inspiration from the human brain.
And train an AI system in two parts.
One part oversees/filters/makes final decisions.
The other suggests actions to achieve local goals.
Ideally this would allow you to train a riskier reward seeking portion using heavy RL.
And a final decision maker using less RL and that has even greater alignment training.
It often feels like something similar happens in our own brains. 
For example, my brain learns where the fridge with food is.
And seeing it will trigger an impulse to get food.
But a second part of my brain comes online and decides is it meal time yet.
It can feel and know the motivation to get food, but still make the correction decision to wait until meal time.
In another example, I don't want to exercise.
And am aware I don't want the pain the comes with exercising.
But my decision making center can take over and decide this is the right thing to do.
One possible counter-argument to this system design is as follows.
A single thinking center or step might be able to do this anyway. 
It might be able to weigh both the possible reward and alignment values.
So, such a two part solution might add complexity or even degrade performance in some cases.
But, part of me still suspects I'd like at least some filter or some guard on AI that isn't heavily RL'ed.
Or at least only RL'ed or alignment related concerns.
A part of the system that's far less likely to have some latent hidden motivations.
Or overly aggressively seek short term rewards.

### Use Tone of Voice Annotations

The idea here is that tone of voice could be useful for help in aligning AI models.
And existing text could be annotated with a tone of voice model.
Essentially every piece of text, generated or source material, could have tone tags attached.
Or even generate audio files using a TTS model.
Adding this additional dimension/metadata to every piece of text could allow for greater filtering and detection.
For example, happiness, deception, fear, and confusion often carry tone signals.
These could be used in conjuction with thinking tokens to attempt to get a better feeling internal "feelings" of AI models.
Tone could be used as a filter for pretraining data.
It could also be used as a filter for outputs. E.g. maybe excessively fearful tone annotated material could be filtered.
Basically, its a way to take existing text and add a tiny peek into what human emotions often occur in such situations.
It obviously wouldn't be perfect or nearly complete. There are many thoughts and feelings that never get experessed in tone.
And the tone annotator could be incorrect, or miss deception sometimes.
But tone annotations could be another incremental tool in our alignment toolbox.

### Removing Duplicate Pathways in Neurons
-- todo

### Adding Steering Neurons at Deeper or Shallower Locations
We have the ability to inject information into a neuron at different locations throughout the network.
For example, we could manually make a certain activation value really large if we wanted a model to rhyme.
And then train the model, so it checks this neuron value to see if the response should rhyme.
If this neuron is deep in the network, the network is likely forced to develop multiple possible responses earlier in the network.
And then choose between them based on the neuron value.
Simply because there is insufficient depth to fully craft a response afterward.
I'm not exactly sure what this capability would be useful for, but it feels like there might be some creative ideas to try.
First you know the model is coniditioning on these values.
Maybe that could make a subregion of the network more interpretable.
You could include many such neurons with a variety of conditions that might make a region even more interpretable.
Second you might be able to use the knowledge that the model is thinking about multiple responses.
Maybe even test for "how many things can the model think about simulteanously."
Anyway, it feels like the use case for this isn't immediately clear cut.
The idea needs more development, but I'll leave it here for reference.



### "Dial Up" a Trait Even Further Than Trained For
It has been shown that you can change model behavior through steering.
And more simply by prompting for specific behaviors.
The idea here is to extend a behavioral change even further than seen during training.
We take a prompt with a numeric value of a trait specified.
And then train the model to do X amount of that trait.
For example, for deception, train the model to be X amount deceptive.
And maybe use an inverted scale so small values correspond to being very deceptive.
And then, at runtime, you crank this value far beyond ever seen in training.
The goal then is that the network has learned to generalize this relationship.
And tries to be even less deceptive than ever seen during training.
While promising, I think there a couple reason this might fail.
First, the model might not generalize this relationship well.
It may learn to interpolate between existing levels of deception.
But fail to extrapolate to new levels unseen during training.
Secondly, I imagine this process could result in weird behavior or other unintended downstream effects.
Finally, having a model capable of extreme deception just laying around could be an added risk.


### Using Inverting Words as Verifiable Rewards

There are many words and phrases that have known logical relationships and functions.
Some words like "not" or "opposite" can invert the meaning of a piece of text.
Or in other cases, antonyms can form a similar function.
We should be able to leverage these logical relationships to develop more deterministically correct training samples.
And do it at scale by automating the process too.
I'm not sure the best way to make use of these properties.
Maybe after developing an alignment reward, you could also invert the reward and invert the wording.
Thus not only pushing the model toward some things, but also pushing it away from others.
Or maybe leverage an approach similar to contrastive learning. 
Where "opposite" samples are pushed apart. 
And "opposite" samples can easily be generated at scale using inverting words to augment existing data.
Another idea: maybe steering vectors can be better tuned using these realtionships.
Or some steering vectors found in a more automated fashion.
For example, maybe you could sample trajectories with and without inverting words applied to the prompt.
And the the "difference" in these activations should be your steering vector.
Any difference captured should be soley attributed to this word flip.
There are some possible weaknesses to this approach.
First, many word interactions and relationships aren't perfectly "clean."
Or may be more complex that the simple logical reduction implies.
Especially when working with imperfect synonyms, for example.
Also, signal learned from such inversions and logical relationships may be more brittle or shallow.
Especially compared to a rich, accurate human-labeled dataset.

### Learn Preference Models for Certain Personalities

Some people have massive amounts of content of them on the internet.
And if the appropriate rights and their permission could be gathered, you might be able to tune a model to their responses.
And if their biases and tendencies were well understood, this might be useful for alignment.
The model of them could be used as a monitor.
Or as a grader.
If it was someone very smart and well respected, and we could sufficiently model their responses, there could be utility there.
If someone, or even a character from a show, was a very bad person, there might still be usefulness as an inverted reward signal.
Hopefully, by narrowing the scope of roles the model has to play, it could be better at indidual roles.
And be more robust/less prone to role-based jailbreaks.
There are definite possible failure modes to this technique though.
Most obviously, the AI might insufficiently model the person's responses.
Also, getting utility without unwanted biases leaking into the final model might be more difficult.


### English Language Autoencoders on Subset of Activations

Neural networks are famously hard to interpret, LLM's especially so.
This idea is to use a encoder-decoder model on part of the activations.
Hopefully, the encoded state will be more interpretable.
The core approach is to force the encoding into English language.
English is fairly powerful for data compression.
And readily interpretable by humans (assuming its well-written).
The idea is to powerfully compress "thoughts" the network is having into English.
The encoder tries to take the incoming activations and encode into language what is happening.
The decoder then is tasked with reproducing the output given just the language.
If the section of network the autoencoder is trying to model is large, the amount of language needed to encode successfully might be quite large.
I suspect a gentle length penalty would be needed.
And also a powerful encoder would be needed. 
Language is famounsly challenging to model -- there's a reason we need such large LLM's today.
Also, there may need to be a judge model adding a reward for readability.
Otherwise the encoder may just learn some complicated mapping that uses words, but doesn't look like nice interpretable sentences.
I think the upsides here are quite tremendous if the approach is effective.
The reward signal for this encoder-decoder is available at massive scale.
(You can train the component over massive pretraining datasets, RL runs, etc).
However, getting it to actually train well is likely tricky.
A concept of compression ratio might be helpful to figure out a science of how much language can compress how much of the nerual network.
Too little language with too many activations likely just won't reconstruct well.
The approach could be extended to multilayer chunks of a neural net too.
The language would then need to encode not just the activations, but the interactions in the encoded layers.
I think some science of what parts, depths, sizes of the network to try to compress would be needed.
Another potential downside is the cost and complexity.
To get good English and reconstruction, a lot of compute might be needed at inference time.
If it's run per token and the encoder-decoder is large, the cost could be significant.
Not to mention, the encoding would then likely need to be run through a separate classifier.
However, maybe this encoder-decoder is still a small fraction of the size of the full LLM and thus not a huge deal.
Finally, I think there are a number of fun ways you could extend the idea.
For example, the encoded state could be images or audio.
