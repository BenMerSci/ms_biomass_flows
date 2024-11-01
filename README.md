Trophic interactions make the backbone of ecological communities [@Bellingeri2016FooWeb; @DeLong2021PreEco; @Wootton2005MeaInt], linking every component through nutrient and energy flows [@Lindeman1942TroAsp].
Consumer-resource interactions of varying strength play a crucial role in shaping important ecosystem functions and processes [@Curtsdotter2019EcoFun; @Koltz2018WarRev; @Duffy2002BioEco; @Montoya2003FooWeb; @Wilmers2012TroCas] such as disease dynamics, invasive species and biogeochemical cycles [@Estes2011TroDow].
Identifying species interactions and quantifying their strength is necessary to understand community composition [@Paine1992FooAna], stability [@deRuiter1995EnePat; @Neutel2002StaRea; @Bascompte2005IntStr; @Nilsson2016IntStr] and the resulting associated ecosystem services [@Montoya2003FooWeb].
Global changes have a diversity of impacts on species themselves, but also how they interact and the resulting assemblages and functioning [@Koltz2018WarRev; @Lurgi2012NovCom].
Empirical observation of these interactions and the evaluation of their strength is however challenging, if not unfeasable due to their sheer amount, sampling biases and the emergence of novel interactions between species that never co-occurred [@Jordano2016ChaEco; @Wootton2005MeaInt; @Aguiar2019RevBia].
The study of ecological networks has therefore recently moved to the development of predictive tools to overcome the limitations associated with empirical sampling of trophic interactions [@Poisot2016DesUnd].
Different models are derived from food web theory, such as the niche model [@Williams2000SimRul], the nested-hierarchy model [@Cattin2004PhyCon], trait-matching model [@Bartomeus2016ComFra] or physical constraints [@Portalier2019MecPre]. 
More recently, @Strydom2021RoaPre developed a general framework to predict interaction probabilities between species in a community context.
These methods are however mostly qualitative, i.e. they are meant to predict if there is an interaction or not, and there is a pressing need to expand them to quantitative interactions, where the strength of interaction between any two organisms is described.

There are many definitions of interaction strength [@Berlow2004IntStr], and among them biomass flows can be particularly suited for the development of predictive models.
Biomass flows between consumers and resources can be derived from functional traits, with the promise of a standardized measure independent of taxa involved [@Berlow2004IntStr].
Quantitative predictive models of biomass flows might also offer potential support to the study of biodiversity and ecosystem functioning relationship, as it seeks to depict all energy flows within communities [@Barnes2018EneFlu].
Biomass flows are defined as a quantity of resource biomass that is consumed by a consumer per unit area and unit of time, reporting how energy circulates through the food web [@Lindeman1942TroAsp]. 
Interaction strengths between consumers and resources is closely related to predation rate in a food web model, namely the functional responses ][@Rall2012UniTem].
Functional response theory aims at describing the change in feeding rate of a consumer, or how many prey or resource a consumer can predate per unit area over time, relative to prey or resource availability [@Holling1959ChaSim; @Holling1959ComPrea; @Solomon1949NatCon].
Where the functional response describes the actual number of individual prey or resource predated by a consumer per unit area over time, biomass flows describes the amount of biomass flowing from a prey or resource to a consumer per unit area over time.
Since both quantities report the rate of the same underlying process that is predation, we anchored the development of our modeling approach in functional response theory.

A fundamental principle underlying the majority of functional responses is the mass action, stating that predator and prey move randomly in an area and encounter at a rate proportional to the product of their abundance and their velocity.
Here we will focus on the two most commonly used types of functional responses.
The type I functional response describes mass action only, where the amount of resource consumed depends on the resource and consumer densities, and the rate (formerly reffered to as attack rate and hereafter space clearance rate [@DeLong2021PreEco]) at which a consumer searches its home range for resources, leading to random encounters followed by detection, attack and consumption.
The type II functional response describes the same process as the type I, but with the addition that consumption saturates with prey availability because of the time required to process prey.
These processes are influenced by a multitude of functional traits and environmental conditions [@Beardsell2021DerPre; @Beardsell2022MecMod].
The space clearance rate parameter varies with consumers and resources intrinsic characteristics such as absolute and relative velocities, perception of the environment and cognitive abilities  [@DeLong2021PreEco].
It is also influenced by externalities such as habitat complexity [@Hall2000OrgMat; @Manatunge2000InfStr; @Barrios-ONeill2016ConSca] and the presence of refugia [@Hoddle2003EffPre] impeding detection probability.
The dimensionality of an interaction, whether it takes place in a two or three dimensional plane, also impacts encounter rates and detection probability [@Pawar2012DimCon; @Pawar2019IntDim].
For instance, a predatory bird searching for preys from above or fishes grazing the benthic surface are examples of 2D planes while aerial insectivorous birds pursuing flying insects or fishes chasing preys in the water column would be in a 3D plane.
Functional response theory therefore makes a good start to develop predictive models of quantitative interactions since widely measured functional traits can be combined with consumer and prey density to predict biomass flows.

The space clearance rate, in units of space per time, reports the amount of area search by the predator in a time interval.
As with many biological processes, the space clearance rate was shown to vary with consumers body mass.
Indeed, multiple studies, summarized in the FoRAGE database [@Uiterwaal2022ForDat], showed an allometric scaling between the space clearance rate and the body mass of consumers.
This observation is coherent with [@Hirt2017GenSca; @Hirt2020RetTro] who documented that the maximum velocity of an organism scales with its body mass.
Handling time is also expected to follow the same scaling relationship [@DeLong2021PreEco], although recent studies are now suggesting that consumers handling time would not be as important at natural resources densities [@Chan2017ImpAss; @Preston2018WhaDri; @Beardsell2021DerPre; @Coblentz2023PreFee].
Ultimately, an accurate evaluation of these parameters is necessary as they are widely used in theoretical models [@Brose2008ForThe; @Pawar2012DimCon; @Brose2006AllSca].
Restraining the parameter space could greatly bonify studies of species coexistence, community stability and trophic regulation.
It could also help the parameterization of global ecosystem models used for biodiversity scenarios [@Harfoot2014EmeGlo}].
Following [@Yodzis1992BodSiz], there are a few meta-analyses looking at the scaling of feeding rates with body-mass [@Rall2012UniTem].
These are however concentrated on a re-analysis of univariate functional responses, mostly from experimental studies, and there is currently no study aiming at reconstructing quantitative interaction networks.

Our main objective is to test if we could model quantitative interactions in complex food webs with easily accessible information such as abundance and body mass. 
We compared statistical models derived from functional response theory, including type I and type II forms.
We also investigate if allometric relationships between space clearance rate, handling time and consumer body mass can contribute to the prediction of biomass flows in diverse food webs.
To do so, we developed four hierarchical models of pairwise quantitative interactions of increasing complexity and evaluated them with empirical data of biomass flows between consumers and resources. 
We curated Ecopath networks [@Christensen2005EcoEco] describing marine, aquatic and terrestrial food webs and extracted 1380 pairwise trophic interactions between consumers and resources. 
Each model represents its own hypothesis and their comparison allow the evaluation of different mechanisms driving interactions.

# Material and methods

A litterature search was performed to gather empirically sampled trophic networks with measurements of biomass flows from resources to consumers, along with population densities.
Food web data are notoriously heterogeneous [@Mestre2022HumDis] and we therefore relied on Ecopath models [@Christensen2005EcoEco] to normalize data collection. 
Ecopath is a modelling software that relies on a mass-balance premiss and a multitude of parameters (production/biomass ratio, consumption/biomass ratio, diet compositions etc.) to provide a realistic static image of the flows of biomass between resources and consumers in an ecosystem [@Christensen2005EcoEco].
It was shown the Ecopath methodology reduces biases in comparative analyses among food webs (Brimacombe, in review).
We therefore collected openly available models from Ecobase [@Colleter2013EcoRep] and worked with a subset of the models present in [@Jacquet2016NoCom].
Taxonomic resolution of Ecopath models is highly variable and it is not uncommon that species are lumped into functional groups.
The models were therefore selected based on the taxonomic resolution with the criteria that most nodes must be resolved at the species level, or that species within functional groups were taxonomically resolved.
We thus curated 19 Ecopath models (detailed list in supplementary material) from aquatic, marine and terrestrial environments ([@fig:network_map]), and trophic guilds spanning from mammal carnivores and herbivores, birds, pelagic carnnivorous and herbivorous fish, demersal carnivorous and herbivorous fish and invertebrates.

![Map of Ecopath models locations used in the present study.](figures/network_map.png){#fig:network_map}

Species identity in the Ecopath models were validated with the original publication and estimates of adult mean body mass was retrived from literature.
Body mass for terrestrial species came from different sources such as the GATEWAy database [@Brose2018GloDat], the original publication for which the Ecopath model was developped or grey literature.
Body mass for marine and freshwater species came from Fishbase [@Froese2023Fis] and Sealifebase [@Palomares2023Sea].
When only body length was available, Fishbase and Sealifebase calculated weight from body length using a bayesian length-weight model.
The midpoint between the minimum and maximum measurements was taken when a mean was not available.
Density (number of individuals per unit surface, $N/\text{km}^2$) was computed by dividing total biomass per unit surface $B$ ($\text{metric tons}/\text{km}^2$) by mean body mass $M$ ($\text{metric tons}$).
The 19 Ecopath models were aggregated in an edge list with quantitative biomass flows ($\text{metric tons}/\text{km}^2/\text{year}$), for a total of 1380 interactions between 154 consumer species and 153 resource species.

## Model description

We developed four different hierarchical models of increasing complexity based on the type I and type II functional responses, and a null model.
Models were then parametrized with Hamiltonian Monte Carlo [@Monnahan2017FasEst], compared and ranked from better to worst based on their prediction accuracy.
The functional form of these relationships are presented below.

### Model 0 - Null model

The null model acts as a basis of comparison with the other models and does not portray any ecological realism of a trophic interaction.
Model 0 hypothesizes that the flow of biomass $F_{ij}$ from a prey $i$ to its predator $j$ is constant with average $K$, irrespective of predator identity:


$$
F_{ij} = K
$$


### Model 3 - Single-species saturating model

Model 3 keeps the assumptions of model 2 with the addition of handling time, thereby representing a single species Type II functional response.
The space clearance rate parameter $\alpha_j$ and the handling time $h_j$ are both consumer-specific:


$$
F_{ij} = \frac{\alpha_j B_i N_j}{1 + h_j \alpha_j B_i N_j}
$$


# References