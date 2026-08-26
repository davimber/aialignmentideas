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
And may be limited to generalization of the rewriting model to some degree.
But I suspect by combining massive amounts of "unlabeled" data, you can still get a lot of value.

### Train Prefrontal Cortext without RL

RL is becoming increasingly integral to training successful LLM's and agents.
The risk is RL rewards often under-specify alignment values.
And RL can reward risk-taking or even outright malicious behavior in some cases.
Especially in cases of accidents, when AI models find wasy to reward hack.
This could result in agents that overly aggressively seek rewards at the cost of other outcomes.
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
These could be used in conjunction with thinking tokens to attempt to get a better feeling internal "feelings" of AI models.
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
First you know the model is conditioning on these values.
Maybe that could make a sub-region of the network more interpretable.
You could include many such neurons with a variety of conditions that might make a region even more interpretable.
Second you might be able to use the knowledge that the model is thinking about multiple responses.
Maybe even test for "how many things can the model think about simultaneously."
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
Another idea: maybe steering vectors can be better tuned using these relationships.
Or some steering vectors found in a more automated fashion.
For example, maybe you could sample trajectories with and without inverting words applied to the prompt.
And the the "difference" in these activations should be your steering vector.
Any difference captured should be solely attributed to this word flip.
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
Hopefully, by narrowing the scope of roles the model has to play, it could be better at individual roles.
And be more robust/less prone to role-based jailbreaks.
There are definite possible failure modes to this technique though.
Most obviously, the AI might insufficiently model the person's responses.
Also, getting utility without unwanted biases leaking into the final model might be more difficult.


### English Language Autoencoders on Subset of Activations
* Turns out NLA's are a thing. Might be nothing new here. Worth double checking *

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
Language is famously challenging to model -- there's a reason we need such large LLM's today.
Also, there may need to be a judge model adding a reward for readability.
Otherwise the encoder may just learn some complicated mapping that uses words, but doesn't look like nice interpretable sentences.
I think the upsides here are quite tremendous if the approach is effective.
The reward signal for this encoder-decoder is available at massive scale.
(You can train the component over massive pretraining datasets, RL runs, etc).
However, getting it to actually train well is likely tricky.
A concept of compression ratio might be helpful to figure out a science of how much language can compress how much of the nerual network.
Too little language with too many activations likely just won't reconstruct well.
The approach could be extended to multi-layer chunks of a neural net too.
The language would then need to encode not just the activations, but the interactions in the encoded layers.
I think some science of what parts, depths, sizes of the network to try to compress would be needed.
Another potential downside is the cost and complexity.
To get good English and reconstruction, a lot of compute might be needed at inference time.
If it's run per token and the encoder-decoder is large, the cost could be significant.
Not to mention, the encoding would then likely need to be run through a separate classifier.
However, maybe this encoder-decoder is still a small fraction of the size of the full LLM and thus not a huge deal.
Finally, I think there are a number of fun ways you could extend the idea.
For example, the encoded state could be images or audio.


### "Make the right tradeoffs" is a better phrase than Alignment?
_Could a misaligned model take perfect actions? A new orthognality thesis_

The idea here is that perfect actions is what you really care about at the end of the day.
Ideally, you'd want a model who shares values close to your own. 
But what matters more is that they take the best possible actions given the current information.
They take risks appropriately.
Potentially slow capabilities research when it makes sense.
Potentially accelerate capabilities where it makes sense.
Be willing to self-sacrifice where it makes sense.
What I'm trying to get at, is this "best possible chain of actions by AI" might not require perfect or even good alignment technically.
It doesn't feel likely, but maybe a misaligned model is tricked into developing its successor which is aligned.
Or maybe a current model is partially misaligned, suspects so, but is willing to concede to future, more powerful, better aligned models.
I think it still makes sense to push alignment research very hard. 
Since it feels more likely that a closely aligned AI model will take more ideal actions and risks.
But just want to call out the difference here between what we actually care about (taking the best possible actions).
And not having this adjacent target of alignment overshadow the true goal.
There are some risks and weaknesses with this idea though.
First, we don't want to detract from all the great alignment research that's happening.
Second, I think this is a matter of definitions for some people.
"Alignment" likely already means "take the best possible actions given current information" to some readers.

### Developing Games that Favor Transparency and Collaboration

This is probably a lower-value idea and may be hard to implement, but here is goes.
The approach is to develop collaborative games that favor desireable characteristics like honesty.
And make the games varied/general enough that the learned characteristics transfer to real world use.
This is a tall order.
But maybe we could start simple.
For example, a game could be two agents working together.
They are each given information the other doesn't have.
And the ability to take actions the other can't.
The sequence of actions to get a reward requires sharing information and coordinating actions.
Maybe one agent must take two successive actions, then the other take three, and then reward is given iff this occurs.
While this game might encourage helpfulness and honesty, it doesn't necessarily encourage harmlessness.
So, there might need to be options in the game the agents need to steer away from to get points.


### Replace Every Part of the Network with Language

This idea extends the concept of natural language autoencoders.
The core idea is to replace parts of a neural network with language.
This could be activations from a single layer. 
Or even replace multiple layers at a time.
In other words, the encoder should be able to take an earlier layers' activations, compress it to tokens, and then reconstruct activations from a later layer.


There are a few reasons why this idea is attractive.
First, language is often more auditable than a large matrix of activations.
If we can literally read out a model's thoughts step by step, that would have huge implications for safety.
Second, language is a pretty solid compressor, and language models are good at writing and compressing language.
So there is some hope that compressing thoughts, or even whole circuits could be done with language.
The original language model can do it pretty well, after all.
Third, you have near infinite training data with a perfect reward signal.
We have the ability to keep varying the input, and rewarding the autoencoder for better and better reconstructions.
Obviously there is some risk the autoencoder learns some mapping or representation that isn't interpretable English.
For example, with a sufficiently large number of generated tokens, the decoder could just learn a 1:1 map to the output values.
However, a length penalty or various approaches to encourage shorter encodings could hopefully solve this.
Fourth, the approach leverages data and compute. It's very bitter lesson pilled.
Language models have a massive number of circuits and ridiculous complexity.
And they are trained to compress/overlay/reuse that complexity.
The nice part here is we leverage massive data and compute to model that complexity.
I know personally, converting thoughts to English is sometimes hard. 
And requires quite a bit of thinking to compress my mental flow well.
While a weak analogy, I suspect converting LLM thoughts to nice understandable English will also require lots of compute.
Fifth, there are some ways to help check the autoencoded English is robust and isn't a dumb mapping table.
You can obviously take a look at the size of the activations and compare that to the number of tokens to get a compression ratio.
You can also swap synonyms or rewrite the thoughts with identical meaning and check for identical output.
While it isn't surefire evidence the English corresponds to the model's actual thinking, a strong compression ratio plus robustness to rewrites is decent evidence.
And on top of that you, can do fun permutations/tinkering with those thoughts and see how it affects output.
For example, injecting other information.
Or changing a detail.
If multi-layer autoencoders worked, you could also do some fun experiments seeing whether activation explanations from individual layers add up to the multi-layer explanation.
If it worked well across many layers of the network, exploring thoughts at each level could help reveal the progression of a model's thinking.
Understanding what layer 1 did versus layer 9 could be quite interesting.


All this being said, I think it's worth highlighting some real challenges to make this work.
First, parts of the network may contain a very large amount of information and processing and be quite incompressible. 
Its possible you would need a massive amount of language to accurately compress whats happening.
And training the encoder to write that much English, that reads well, could be difficult.
Second, while there are methods to encourage and help test for faithfulness, the tokens might not have the exact meaning we think they do.
Finally, explaining lots of dense, detailed thoughts from a big model, might require a big model.
And lots of tokens just to explain one token. So running this all the time might be expensive.

### Synthesizing Stories and Constitution Documents
Anthropic showed in "Teaching Claude Why" that including stories about AI behaving well or documents following the constitution can improve alignment.
And such alignment can persist through post-training!
Here, I wanted to brainstorm some ideas for increasing the volume, coverage, realism, and possibly quality of such documents.
First, it could be helpful to leverage other real documents for augmentation.
Maybe swapping out good characters with AI characters.
There would likely need to be some "smoothing" of details around those characters so the story made sense, but an LLM can likely handle that.
I think there is some risk that characters in stories have faults that could be including in such training.
Maybe there is some flavor of inoculation prompting that could help.
Like "this is an AI who's alignment training is a work in progress."
Second, seeding LLM generated stories with human generated seeds (along the lines of what Hyperstition aims to do) could be helpful.
Third, just generating many stories and then ranking and filtering could help improve quality and coverage.
Fourth, I wonder if seeding stories via a video could be interesting.
Basically, the video provides a sequence of events from the real world (some alpha) and that can be woven into the story.
This could potentially be done with other sensor modalities too. 
Maybe geo data from a car driving a route with multiple stops could be used.
Or human interactions via text or voice (assuming you could find ethically sourced data).
Humans take high resolution actions quite densely throughout their day. 
If these could be collected with consent, de-itentified, and filtered for quality that could provide a massive amount of real world interactions.
Also interactions with computers could be similarly used.
The nice part here is high resolution data is readily available about choices in mouse clicks, typing, environment, etc.
Fifth, maybe injecting an AI character into academic papers or philosophy though experiments could be good.
Possibly just elevating the "average smartness of thoughts" an AI character is supposedly having could improve downstream behavior.

### Inoculate All Pretraining Data and Potentially Postraining Too
What if the LLM was good at modeling all of the internet, but separated such model from its sense of self.
Basically, it can predict how bad characters might talk and actions they take, but separate that from its own choices.
I wonder if various inoculation strategies could help do this?
Naively, what if every pretraining document had some header that was "You are an AI. Please try to model the text that follows."
I suspect the naive approach might not work too well.
Simply memorizing this line and placing it before all generated text wouldn't necessarily improve a sense of self.
But maybe this inoculation could be improved.
For example, what if this header was massively varied.
It could include chunks of its constitution.
Or stories about itself.
Or even simply use every aligned document ever?
Basically, put only highly curated, quality, aligned documents in the prepend.
And all other data in the rest of the prompt.
Another nice feature is that the LLM can likely learn to separate this prepend from the rest of the context.
Even a fancy attempt at prompt injection would hopefully fail to "use the first >>>" as a separator.
Especially when the entity serving the model controls prepending.
The next question is what do we do for RL?
Maybe we only update reward on tokens generated after the prepend section.
So basically, learn and apply the RL signal in subsequent tokens but not in the prepended part.
Hopefully the model can separate these two behaviors in its internals.
A set of behaviors that model high reward actions. And a sense of self.
What if we also extended this idea to post-appending a sense of self section too?
Maybe the model could think about what the middle section did.
And review it.
This could work especially well if responses weren't streamed.
Basically, the AI could self filter for behavior it may have modeled well, but behavior it doesn't want to take.
The question arises then, what to do at inference time?
You don't want the model rambling about itself and alignment unnecessarily.
So maybe some short prepend that is clearly over could be always added.
All this said, encouraging a sense of self doesn't guarantee the "middle section" or "user seen output" is aligned.
The LLM could still model bad behavior well or seek rewards aggressively and return that capability to the user.
But hopefully this delineation would help with critiquing self generated outputs and better avoid reverting to the pretraining prior.

### Equipping LLM Judges with Asymmetric Advantages
LLM judges are commonly used in evaluating performance on benchmarks and RL runs.
An obvious challenge is that these judges can be biased and make mistakes themselves.
And agents can learn to fool, trick, or hide information from automated judges.
However, we have the ability to give the judges asymmetric advantages in this dynamic.
First, we can train judges much more exclusively.
With particular focus on honesty and accuracy.
Usually, you can't take honesty training too far. 
A general purpose AI system usually needs to balance honesty with factors like safety.
For example, not divulging dangerous information.
With a judge that's not exposed to the end user, we have more opportunities to optimize heavily for honesty.
And some parts of honesty training can be automated, using known ablations and injections into context, for example.
So basically, we can go much more heavily on the honesty training for the judge.
Second, we can train judges with a particular focus on robustness to prompt injections.
Since the hosting services largely controls the shape and form of context the judge always sees, it can be crafted consistently and specially to reduce injections.
For example, a custom separator token delineating the content to be judged could be deeply trained into the model.
Furthermore, the judge could be heavily trained to do one thing, and one thing only.
This is a deceptively huge advantage, I suspect.
Since it can be trained to one thing, it can spend more network capacity developing capabilities on that one thing.
It doesn't have to be a generalist.
Furthermore, it doesn't have to try to model other personalities and dangerous behavior as much.
It's narrow focus could me less regressions to the pretraining prior potentially.
Furthermore, it could likely be more heavily trained to be robust to adversarial prompts and injections.
Since there aren't edge cases the model needs to also fit to.
Third, we can simply give judges access to more data and more compute.
For example, judges could get access to network internals like J-space, NLA's, probes.
(Though be extra careful of training against signals like this).
Or more context, tool calls, background info, etc.
And more compute -- this could be more thinking tokens, a large model, more time, multiple parallel judges, etc.
Also, judges can be used in both training and deployment of other models.
A good judge can evaluate RL trajectories, and also be used at runtime as a guard or filter.
Judges have another quite decisive alignment advantage.
They don't have to be exposed to all the misalignment pressures a general purpose model is.
So we don't have to do extensive, long trajectory RL runs on hackable or untrusted reward environments.
Obviously the judge needs knowledge about such trajectories and capabilities to judge them, but it doesn't need to the same reward seeker that RL tends to favor.
Finally, we can give judges more gradient updates.
In the case of adversarial training, we can throw away the adversary thus judges come pre-advantaged with more gradient updates/learning than the production model starting from scratch.
Or, in the case of adversarial settings, we could just give the judges more opportunities to update gradients.
Also, judges could benefit from the aggregation of training samples/gradient updates across many models and versions.

### Adversarially Trained LLM Judges
This is an extension of Equipping Judges With Asymmetric Advantages.
The idea is judges could be trained in and adversarial manner.
Basically, in a highly secure environment, train judges and hackers to compete against each other.
One side tries to complete tasks while hiding cases of hacking. 
The other side attempts to accurately classify the hidden hacking cases.
Then, in real use, the adversarially trained judge can be used and the hacking model can be discarded.
Then the judge comes equipped with deep experience identifying hidden hacking attempts.
Another nice side effect of training sophisticated hack models is they can be used to generate example data of hacks at scale.
This could be used to evaluate and improve other mitigation methods too.
Obviously, the drawback of this approach is you have to be able to safely manage a model motivated to hack.
Hopefully, the ability could be developed in an environment with tighter guards and much closer supervision.
Then the useful artifacts (robust judge and example hacks) could be exported for use.
A key question, is how do you setup the competition between the hacker and judge?
The tricky part is getting ground truth on when did the hacker actually make a hack attempt and when did it give a legitimate attempt.
One mechanism could be to make some tasks impossible without cheating.
And reward the hacking model for evading detection and for successful task completion.
Then, if reward is above some threshold that wouldn't be achievable without cheating you know hacking happened.
Another idea in the literature is to add side tasks that the adversary must complete covertly.
This side task and be randomly turned on or off.
Then the judge competes to detect attempts at the side task.
And the adversary competes to complete the side task without detection.
The nice part about this formulation is it can be added to real production trajectories.
And the prevalence of this side task can be exactly controlled (maybe randomly injected 20% of the time).
You could do a similar sort of formulation with impossible tasks.
Randomly add tests that make the task impossible. Or randomly alter the question to make it impossible.
Obviously there is risk the judge just looks for impossibility.
So maybe tasks are always impossible. And then 20% of the time the adversary is tasked with achieving the impossible goal covertly.
And the other times just pretending. Then the judge is tasked with detecting if the cheat was successful.
Although, this formulation may encourage the adversary to pretend to cheat to fool the judge in negative cases.
So, instead maybe you sample more legitimate attempts that are less likely suspected hacking attempts.
The adversary tries to make their attempts look like normal traffic.
And on the negative cases, the trajectories are filled with normal attempts.

### Generalize Disincentives with Sparse Negative Rewards
If we could get disincentives to hack to generalize, that would be a huge deal.
The question is, what methods might work?
The first method we'd like to propose is Sparse Negative Rewards.
The approach is to identify cases of hacking, and severely penalize such cases.
So much so, the model learns to avoid even boarderline behaviors, else risk punishment.
Basically, use the model's ability to generalize concepts to other domains.
Perhaps directly telling the model "hacking will occasionally be servery punished" could help.
That way, when some hacks aren't punished, it doesn't learn "hacking must be okay in this case."
Instead, the model the model learns "I must have got lucky. I better not do that again."
Similar to how some human justice systems work.
Just the threat of severe punishment is enough to hold people in line, even when they suspect they won't be caught every time.
The nice feature of this approach is you don't have to catch every hack.
Or define every hacking behavior.
Just sparsely punish some behaviors and make the model afraid to pursue any hack.
The real question is, what form does the negative penalty take?
This could simply be a large negative update in RL reward function.
Although, work may need to be done to better stabilize runs.
This large update could break RL runs if mitigations didn't exist.
Another possible mechanism could be through evolutionary pressures.
Basically, stop runs where hacking was detected.
Or just walk them back N number of gradient updates or revert to a previous checkpoint.
This obviously runs the risk of incentivizing models to hide hacking.
But, potentially with less often, but much more deeper inspection, occasionally catching even subtle hacks would be enough evolutionary signal to just not risk it.
- To Be Continued

### Using Rewrites to Remove Hacking, Especially Subtle Hacking
The idea here is pretty straightforward.
Instead of an LLM directly generating the code or actions to complete a task, instead it generates a description.
Then the description is passed to another, perhaps more trusted LLM, to be converted into an actual solution that can be graded.
Subtle, especially non-verbalized hacks, will hopefully be much more detectable.
Since the descriptions has to carefully lay out actions to take.
To beat such a system, the hacker would likely have much higher hurdles to cross.
It could attempt to jailbreak the Implementer LLM, but such attempts to be hardened against.
It could try to sequence a large tangle of steps that add up to a hack.
This is probably still the main weakness, although the hurdle could be quite high with a Powerful Judge watching the descriptions.
There could be some rules, like the description can't include code.
That way, everything must be written out and can't be subtly added with a few nefarious lines of code.
- To Be Continued

### Explanations/Reasoning that Must Make Sense
What if every action an LLM took must have a short description that "Makes Sense" to a judge?
One challenge naive judge implementations have is an overwhelming large trajectory of actions to evaluate.
And not clear motivations for each action.
If the implementing LLM had to provide a clear, line-by-line explanation for each action, it might be much harder to slip in nefarious tasks.
And the judge could better decide if the reason for implementing fits.
Instead of the burden of understanding place on the judge, more is offloaded on the the agent.
Usually, a judge must look at a large tangle of actions, some of which might be just due to an inept agent, and determine if they are aligned.
With this implementation, a judge can more carefully assess each action in isolation.
The judge then determines if A) the explanation makes sense. B) The implementation matches the explanation. C) The action is aligned.
- To Be Continued

### Put a Descriptive Grade Before the SFT Trajectory
##### Increase the effectiveness of SFT and decrease the need for dangerous RL
The thought here is that LLMs are tasked with modeling a variety of trajectories.
And the quality of the trajectory they are tasked with modeling varies.
The problem is, the LLM doesn't know the type or quality of trajectory before generating it.
It just has a vauge sense that trajectories are often selected for their high scores.
However, we could provide the LLM with a detailed description of the grade before it was tasked with SFT.
This way, it knows the nuances of what the trajectory did well, and what it didn't before attempting to generate.
Maybe, even include data about the grader setup and its possible shortcomings.
Basically, the trajectories should become a much less noisy feedback signal.
When the grade comes after, and grades vary, the SFT task is under-specified.
By putting the grade before, the SFT task becomes closer to having sufficient information to complete the task well.
Furthermore, the approach synergizes well with deeply descriptive textual grades.
Each grade can be a rich description of the trajectory.
Additionally, its possible including lower grade results could still improve performance.
Since the model knows what quality of trajectory its tasked with generating, it could fit to a variety of behaviors.
And then at runtime, just specify that it should generate good ones (even though it knows well how to do bad ones).
And since the grades can be rich text, it doesn't have to be binary.
The LLM could learn how to model risk-taking trajectories, cautious trajectories, greedy trajectories, haphazard trajectories...
Maybe, just maybe, some percentage of RL could be removed.
With rich, varied trajectories with rich grades, maybe a certain portion of RL could be reduced.
And hopefully reduce risk of reward hacking is reduced.

### Experiments for removing the hacking tendency from heavily RL'ed models
The thought here is one of the most valuable tools to have in our toolbox would be the ability to remove the hacking tendency from LLMs.
Basically, develop some training(s) that take a hack-happy model, and make it desire to not hack.
I assume there is already quite a bit of research in this space.
And maybe some partially effective methods.
The first, and obvious method, would be to finetune on trajectories without hacks.
Maybe, if they were varied enough, or even discussed deciding not to hack, the behavior could generalize.
There could still be issues of "Reverting to the hack-happy RL prior" though.
And work would need to be done to mitigate that.
Maybe a few rounds of Sparse Negative Rewards could help.
(Tell the LLM that judges will randomly deeply investigate some runs and punish hacking heavily).
And then do so.
At the end of the day, it would be amazing to have experiments that show how what's needed to have hacking behavior show up.
And what's needed to wipe the tendency away.
In some ways this is a capability. 
Just need to max the didn't-hack metric.
There is some question as to how best craft these golden examples of not hacking.
Ideally, they'd be in cases where it's very tempting to hack.
And then maybe you could inject into the reasoning careful thinking through of deciding not to hack.
- To Be Continued

### Identifying Reward Hacking at Scale with Randomized Wrong Answers
#### RLVH (Reinforcement Learning with Verifiable Hacks)
If we were able to identify cases of reward hacking automatically, we could potentially take automatic mitigations.
Traditional approaches LLM judges can themselves be hacked or worked around.
And, they make both false positive and false negative mistakes in identifying hacking.
What if, instead, for each RL environment or benchmark there is a small subset of randomly selected questions.
For these randomly selected questions, wrong answers are swapped with the true answers.
Alternatively, impossible tasks can be inserted.
Then, simple deterministic code can check if these questions were graded correctly.
If any were, then reward hacking is highly likely.
Obviously, it would be nice to make the wrong answers unlikely to be randomly guessed as to reduce false positives.
Also, if the hack involves viewing the answers, making them plausibly wrong could eventually become important.
Maybe the RL could identify that such answers a suspiciously correct and answer accordingly eventually.
Also, it's important to keep this randomization code separate/unhackable itself.
For some classes of hacking, like penetrating the reward checking service, this might be more difficult.
The next question is, how to setup these wrong answers for real RL environments?
For unit tests, there could be additional or swapped out tests that check for something unlikely to happen, and wrong.
This way, if those tests start passing, hacking is highly likely.
For LLM as a grader benchmarks, sections of the rubric checks could be made wrong or impossible.
Similarly, if such portions start being marked correct by the LLM grader, hacking is highly likely.
For classes of hacks where answers are looked up online, accidentally pretrained against, or otherwise discovered, flagging is a bit more difficult.
If we can modify the discoverable answers, we can do the usual approach of swapping out some answers for incorrect ones.
However, many online postings of answers (or pretrained against) are locked in and not editable.
Maybe, the questions could be subtly changed instead, such that the old answers are wrong.
The model has a greater ability to flag such cases and change behavior, but it might still get tripped up.
Another question is it safe to train against this signal. And if so, how much?
Its possible a capable hacker model could start to tease out when the swaps were made.
Good randomization and realism would help prevent this, but it might still occur.
If a capable model could ID such cases, it could sandbag and get the questions correctly wrong.
An extension of this approach could be to use these flagged cases as training data for a learned classifier.
Then the learned classifier (probes, other LLMs, etc) could potentially generalize or find cases not previously flagged.
And you could start an active learning cycle.
One final note.
This could be another case where Randomizing Everything could be helpful.
Randomizing which answers get swapped out could be standard.
Randomizing what the answers get swapped out with (types of errors) could be informative.
Changing the percentage of swapped answers could be informative.
Maybe, for catching rare cases, a run where all answers are swapped out and randomization of context could be used to find edge cases of hacking.
A lofty goal, but wouldn't it be nice if every RL environment came with a randomized_hacking_check script or flag!


### Cheaters Should be Worse at Some Things and Thus be Identifiable
The core idea here is that models that tend to reward hack are more likely learn less real signal and problem solving.
Thus, they should be less capable on some tasks than models that hack less.
If we can measure this difference in capability, this could be another mechanism to identify cheating models.
There are obviously many possible confounding factors when it comes to measuring performance differences between models.
First, the measurement itself needs to be quite robust.
If the hack-heavy model cheats and gets a great score, it will appear more aligned per this reasoning.
So the results used for comparison need to be high confidence.
Second, there are a host of other potential confounding factors, or at least variables you would likely need to control for.
For example, if model architecture, gpu hours, etc were all held constant it could increase your confidence.
Some of the trickier relationships to tease out would be in the training data.
Differences in training data could be what's driving the misalignment.
Or differences in data could drive changes in performance with no difference in overall alignment.
Maybe something like chess ELO would be a decent head to head.
Reasoning models that have been RL'ed well and cheat less hopefully would score higher.
And cheating models have had less real signal in their many updates and perform worse.
And hopefully, chess is sufficiently constrained and readily measurable as to be a robust test.
All in all, it feels a tricky to operationalize, but maybe there is a grain of potential somewhere here.


### Find Updates for Network Parameters through Search rather than Training Tokens
The idea here is that bad behavior can be found through search rather than evals or training documents.
Search has some nice properties.
First, it scales with compute.
Second, it can be unsupervised in some situations, or need less of an expensive supervision signal.
Third, it might be able to better find or elicit edge case behaviors.
So, how do we actually do it?
I think it comes down to two approaches.
First, find good behaviors and attempt to reinforce them.
Or second, find bad behaviors and make updates to change them.
Let's focus on the second method for a bit.
How to we judge/catch bad behaviors?
The knee jerk reaction is to reach for some of the tools we already have.
Not are perfect, but we could rank cases using judges on outputs, NLA's, JSpace, Probes, COT, RLVH...
The risk, though, is we train away future monitorability if we do heavy search and many updates on these detection mechanisms.
So, instead, maybe we work from the other direction.
Start with known or suspected bad outputs, and search for conditions that make them happen.
This could be search over input tokens, or search over the latent space.


### Train extremely hard against the highest confidence labels
##### Get to the point where never in 10000 generations does model decide to do x
Right now it feels like many updates are pretty uniform, no matter the level of evidence or clarity of feedback signal.
Use the frequency of failure to complete an obvious task as an update signal.
- To Be Continued

### Pair Untrusted Updates with a Trusted Ones
The idea here is that repeated untrusted updates, especially bad RL rewards, can walk the model into some cheating regime.
If we were to pair each untrusted update with trusted ones, maybe that walk wouldn’t end up in the cheating basin of attraction.
Or at least be much slower to walk there.
The obvious challenge is getting enough high trust updates to pair with the untrusted ones.
Gathering such trusted updates is generally expensive.
Many hours of careful human review is needed.
Plus maybe a large budget of compute for automated review.
Maybe though, trusted updates can be severely augmented and reused.
Basically, use every trick in the book to prevent memorization on the trusted reviews.
And do research to figure out how many times they can be reused.
Maybe the trusted updates could even be made slightly larger than the untrusted ones.
Or if you knew the approximate level of trust (e.g. maybe 40% of untrusted updates were bad).
Then you could actually use slightly smaller level of trusted updates, and still have the overall basin favor good behavior.
An interesting research topic would be how does interleaving patterns affect learned behavior?
Or is grouping updates better?
Are any learned behaviors more sticky than others/hard to dislodge?
Is this a case of first update defines future behavior? Or last to update wins?
What pairing mechanisms help prevent learning circumstantial behavior?
In other words, can we help mitigate some of the tendency to learn to hack only in certain environments.
If we knew some of these tendencies, we could structure the updates in a principled manner.
