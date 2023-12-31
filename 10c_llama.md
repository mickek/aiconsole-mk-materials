<!--- Use this material to retrieve information about llama technology and services -->

LLaMA (Large Language Model Meta AI) is a family of large language models (LLMs), released by Meta AI starting in February 2023.

For the first version of LLaMa, four model sizes were trained: 7, 13, 33 and 65 billion parameters. LLaMA's developers reported that the 13B parameter model's performance on most NLP benchmarks exceeded that of the much larger GPT-3 (with 175B parameters) and that the largest model was competitive with state of the art models such as PaLM and Chinchilla.[1] Whereas the most powerful LLMs have generally been accessible only through limited APIs (if at all), Meta released LLaMA's model weights to the research community under a noncommercial license.[2] Within a week of LLaMA's release, its weights were leaked to the public on 4chan via BitTorrent.[3]

In July 2023, Meta released several models as Llama 2, using 7, 13 and 70 billion parameters.

LLaMA-2
On July 18, 2023, in partnership with Microsoft, Meta announced LLaMA-2, the next generation of LLaMA. Meta trained and released LLaMA-2 in three model sizes: 7, 13, and 70 billion parameters.[4] The model architecture remains largely unchanged from that of LLaMA-1 models, but 40% more data was used to train the foundational models.[5] The accompanying preprint[5] also mentions a model with 34B parameters that might be released in the future upon satisfying safety targets.

LLaMA-2 includes both foundational models and models fine-tuned for dialog, called LLaMA-2 Chat. In further departure from LLaMA-1, all models are released with weights, and are free for many commercial use cases. However, due to some remaining restrictions, the description of LLaMA as open source has been disputed by the Open Source Initiative (known for maintaining the Open Source Definition).[6]

Architecture and training
"A conversation between the sun and pluto"
Sun: Hey Pluto, what’s up?
Pluto: Not much. Just hanging out here at the edge of the solar system.
Sun: Yeah, I’ve been meaning to talk to you about that. You’re not a planet anymore.
Pluto: What? Come on, man. That’s not fair.
Sun: I’m sorry, but it’s true. You just don’t meet the criteria anymore.
Pluto: This is bulls**t! I’ve been a planet for over 70 years!
Sun: Things change, Pluto. You’ve just got to accept it.
Pluto: F**k you, Sun! F**k you and your stupid solar system!
– Output of 65 billion parameter LLaMA model after instruction tuning given the prompt "Write a conversation between the sun and pluto"[1]
Architecture
LLaMA uses the transformer architecture, the standard architecture for language modeling since 2018.

There are minor architectural differences. Compared to GPT-3, LLaMA

uses SwiGLU[7] activation function instead of ReLU;
uses rotary positional embeddings[8] instead of absolute positional embedding;
uses root-mean-squared layer-normalization[9] instead of standard layer-normalization.[10]
increases context length from 2K (Llama 1) tokens to 4K (Llama 2) tokens between.
Training datasets
LLaMA's developers focused their effort on scaling the model's performance by increasing the volume of training data, rather than the number of parameters, reasoning that the dominating cost for LLMs is from doing inference on the trained model rather than the computational cost of the training process.

LLaMA 1 foundational models were trained on a data set with 1.4 trillion tokens, drawn from publicly available data sources, including:[1]

Webpages scraped by CommonCrawl
Open source repositories of source code from GitHub
Wikipedia in 20 different languages
Public domain books from Project Gutenberg
The LaTeX source code for scientific papers uploaded to ArXiv
Questions and answers from Stack Exchange websites
Llama 2 foundational models were trained on a data set with 2 trillion tokens. This data set was curated to remove Web sites that often disclose personal data of people. It also upsamples sources considered trustworthy.[5] Llama 2 - Chat was additionally fine-tuned on 27,540 prompt-response pairs created for this project, which performed better than larger but lower-quality third-party datasets. For AI alignment, reinforcement learning with human feedback (RLHF) was used with a combination of 1,418,091 Meta examples and seven smaller datasets. The average dialog depth was 3.9 in the Meta examples, 3.0 for Anthropic Helpful and Anthropic Harmless sets, and 1.0 for five other sets, including OpenAI Summarize, StackExchange, etc.

Fine-tuning
Llama 1 models are only available as foundational models with self-supervised learning and without fine-tuning. Llama 2 – Chat models were derived from foundational Llama 2 models. Unlike GPT-4 which increased context length during fine-tuning, Llama 2 and Llama 2 - Chat have the same context length of 4K tokens. Supervised fine-tuning used an autoregressive loss function with token loss on user prompts zeroed out. Batch size was 64.

For AI alignment, human annotators wrote prompts and then compared two model outputs (a binary protocol), giving confidence levels and separate safety labels with veto power. Two separate reward models were trained from these preferences for safety and helpfulness using Reinforcement learning from human feedback (RLHF). A major technical contribution is the departure from the exclusive use of Proximal Policy Optimization (PPO) for RLHF – a new technique based on Rejection sampling was used, followed by PPO.

Multi-turn consistency in dialogs was targeted for improvement, to make sure that "system messages" (initial instructions, such as "speak in French" and "act like Napoleon") are respected during the dialog. This was accomplished using the new "Ghost attention" technique during training, that concatenates relevant instructions to each new user message but zeros out the loss function for tokens in the prompt (earlier parts of the dialog).

Release and leak
LLaMA was announced on February 23, 2023, via a blog post and a paper describing the model's training, architecture, and performance.[1][2] The inference code used to run the model was publicly released under the open-source GPL 3 license.[11] Access to the model's weights was managed by an application process, with access to be granted "on a case-by-case basis to academic researchers; those affiliated with organizations in government, civil society, and academia; and industry research laboratories around the world".[2]

On March 2, 2023,[12] a torrent containing LLaMA's weights was uploaded, with a link to the torrent shared on the 4chan imageboard and subsequently spreading through online AI communities.[3] That same day, a pull request on the main LLaMA repository was opened, requesting to add the magnet link to the official documentation.[13][14] On March 4, a pull request was opened to add links to HuggingFace repositories containing the model.[15][13] On March 6, Meta filed takedown requests to remove the HuggingFace repositories linked in the pull request, characterizing it as "unauthorized distribution" of the model. HuggingFace complied with the requests.[16] On March 20, Meta filed a DMCA takedown request for copyright infringement against a repository containing a script that downloaded LLaMA from a mirror, and GitHub complied the next day.[17] As of March 25, Facebook has not responded to the pull request containing the magnet link.[14]

Reactions to the leak varied. Some speculated that the model would be used for malicious purposes, such as more sophisticated spam. Some have celebrated the model's accessibility, as well as the fact that smaller versions of the model can be run relatively cheaply, suggesting that this will promote the flourishing of additional research developments.[3] Multiple commentators, such as Simon Willison, compared LLaMA to Stable Diffusion, a text-to-image model which, unlike comparably sophisticated models which preceded it, was openly distributed, leading to a rapid proliferation of associated tools, techniques, and software.[3][18]

Dataset reproduction
On April 17, 2023, TogetherAI launched a project named RedPajama to reproduce and distribute an open source version of the LLaMA dataset.[19] The dataset has approximately 1.2 trillion tokens and is publicly available for download.[20]

Applications
The Stanford University Institute for Human-Centered Artificial Intelligence (HAI) Center for Research on Foundation Models (CRFM) released Alpaca, a training recipe based on the LLaMA 7B model that uses the "Self-Instruct" method of instruction tuning to acquire capabilities comparable to the OpenAI GPT-3 series text-davinci-003 model at a modest cost.[21][22] Multiple open source projects are[when?] continuing this work of finetuning LLaMA with Alpaca dataset.[23]