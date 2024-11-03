# syur.my

## Description of current ideas

ZKML runtime based on loGKR proof system

I'm looking into implementing next generation ZKML proof system (currently focusing on LoGKR), I don't have any money to pay the hackers or resources besides myself but I think I have a good thing going. I won't be inviting investors on this unless I have to but I'm accepting donations and grants in any form. I'm undergoing the best training available on these topics (from the Kung Fu masters at Antalfa and Invisible Garden partners, besides my formal education and 15+ years of professional experience) and have the best mentors, if I don't have to find a job to sustain myself I might produce some good results for the world.

Basically right now I'm researching the ways to adapt LogUp + GKR proof system to be used in a ML inference runtime which is something that has already successfully been done for ZK-VMs (e.g. Jolt) and has some cryptographic tooling for acceleration (e.g. ICICLE v3) and has some research and even reference implementations (zkCNN, zkLLM are both slightly different but can be used as good examples) so it's only a matter of implementing a good middle layer between research cryptography + acceleration libraries on one hand and ML inference runtimes and their acceleration tech on the other.

There are multiple possible core protocol optimizations. Apart from loGKR that improves LogUp significantly, there's Power Ciruits and other ideas like that. Plus there can be simple enough optimizations possible on the library level (I've seen people optimizing arkworks and other core libs for orders of magnitude improvements). I cannot yet provide any projections until there's a PoC to benchmark but I think a lot of things can be done right to make things run real fast.

Integrations are something I'm personally good at (optimizations too), last fifteen years of my career was spend integrating various pieces and bits of tech and I can quickly learn advanced concepts of ZK cryptography and any advanced ML acceleration to figure out the most practical way to optimise the bottlenecks. I can hack this, it's only a matter of time and resources. Open to offers, donations, grants, invites, talks but ideally I want to build it the way I want and let it be free for the world to use (dedicating all my personal contributions to public domain or licensing openly/freely whichever is better) and prioritize types of support that's aligned with that vision. I'm currently exploring hackathons I could win with something ZKML-centric, that comes with zero string attached but takes fair amount of time I'd rather spend reading articles and writing code.

Again, unless I absolutely have to I'd prefer to avoid any kind of investors looking into making it a closed product of any kind, I want to build a generic open-source tool, available for eveyone to use or hack, I will not be extorting money by enshittification, if I don't find support, I'd rather go back to freelancing web2 backends putting all of this on pause.

### Some previous work

[STW23] {lasso} https://eprint.iacr.org/2023/1216

https://jolt.a16zcrypto.com/

[PH23] {loGKR} https://eprint.iacr.org/2023/1284

[Soukhanov23] https://eprint.iacr.org/2023/1611

[LXZ21] {zkCNN} https://eprint.iacr.org/2021/673

https://github.com/TAMUCrypto/zkCNN

[SLZ24] {zkLLM} https://arxiv.org/abs/2404.16109

https://github.com/jvhs0706/zkllm-ccs2024

(Custom proof system for LLaMa inference.)

https://ezkl.xyz/

(Arguably one of the more practical runtimes. Still limited, not FOSS anymore.)

https://medium.com/@ingonyama/icicle-v3-1c9cc2f94402

(Acceleration library for ZK proofs, now backend agnostic)

https://github.com/ingonyama-zk/icicle/releases/tag/v3.0.0

### More research

[CYY24] {zkMatrix} https://eprint.iacr.org/2024/161

This actually shows good results for matrix multiplication specifically, I tested benchmarks. It could prove useful for ML-related operations, much of them can be decomposed into batches of simple matrix operations, with Einstein notation and possibly this

https://github.com/sonos/tract

(A tool to optimize and declutter ML models. EZKL use this approach instead of having custom proof systems for each operation.)

Also on the LogUp+GKR front I reviewed and tested implementation in winterfell

https://github.com/facebook/winterfell/pull/302

(Hard to estimate if it's hard or easy to apply sqauring circuits optimization there but it's worth another look.)

### Rough execution plan breakdown

1 - Core research and PoC

We are currently here (will be for a while, with no support I'll be slow and distracted, which is maybe okay actually, it starts feeling like this is going to take a while a needs a pause to think and regroup). I've seen some very practical applications of sum-check (lasso+jolt) and quite impractical ZKML provers. My believe is it's not that hard to hack loGKR or similar protocol to suit ZKML inference needs and PoC runtime supporting just a couple simple operations can be produced in a few months of work and benchmarked against other implementations (RMSNorm is pretty common, for example, I'd start there)

My very first step is to read and reread those articles in the references and then some more and try to see and test each cool thing in code. An attempt to make zkMatrix for a simple tensor operation and a lookup argument for some other will be the next but we are not there yet.

2 - Active development

Once we figure out the core protocol adding a proper runtime with feature parity against competitors will require some dedicated work of a larger team. Luckily there are some examples of ZKML runtimes already, we won't be flying blind, it's just a lot of new code, test cases, optimization, etc.

3 - The Bright Future

Once there is a runtime though, all the good use cases for ZKML can be tested. Hopefuly (provided our implementation has good performance) proving some bigger models than is currently pracical. Basically a bunch of products from on-chain gaming to DeFi can be created or improved. Then further research can include proof of training (still challenging part of ZKML, considered mostly impractical with the current tech) apart from, obviously, on-going performance optimization work.
