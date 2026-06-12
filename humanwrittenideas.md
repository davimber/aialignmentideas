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

