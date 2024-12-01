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

$$F_{ij} = K$$

### Model 1 - General mass action

Model 1 implements a general version of the type I functional response and thereby focuses on the law of mass action.
The flow of biomass $F_{ij}$ depends on the available prey biomass $B_i$ and the abundance of the predator $N_j$ where they encounter each other at a given the $\alpha$ space clearance rate of the consumer $N_j$.
Explicitely, only the consumer's mobility is considered as it searches for resources.
For the purpose of comparison, model 1 hypothesizes that all consumers have the same space clearance rate $\alpha$:

$$F_{ij} = \alpha B_i N_j$$

### Model 2 - Consumer-specific mass action

Model 2 follows the previous one with the hypothesis that space clearance parameter $\alpha_j$ is a specific parameter for each consumer species $j$:

$$F_{ij} = \alpha_j B_i N_j$$

### Model 3 - Single-species saturating model

Model 3 keeps the assumptions of model 2 with the addition of handling time, thereby representing a single species Type II functional response.
The space clearance rate parameter $\alpha_j$ and the handling time $h_j$ are both consumer-specific:

$$F_{ij} = \frac{\alpha_j B_i N_j}{1 + h_j \alpha_j B_i N_j}$$

### Model 4 - Multi-species saturating model

Building on model 3, model 4 implements a multi-species version of Type II functional response [@Smout2010FunRes]. 
Parameters are the same as the ones used in model 3, the difference is found at the denominator where handling is aggregated over all species in the food web: 

$$F_{ij} = \frac{\alpha_j B_i N_j}{1 + h_j \alpha_j \sum_{i=1}^{nprey}B_i N_j}$$


| Model name                      | Model equation                                                                 | Number of parameters |
|---------------------------------|--------------------------------------------------------------------------------|----------------------|
| Null model                      | $F_{ij} = K$                                                                   | 2                    |
| General mass action             | $F_{ij} = \alpha B_i N_j$                                                      | 2                    |
| Predator specific mass action   | $F_{ij} = \alpha_{j} B_i N_j$                                                  | 157                  |
| Single species saturating model | $F_{ij} = \frac{\alpha_j B_i N_j}{1 + h_j \alpha_j B_i N_j}$                   | 313                  |
| Multi species saturating model  | $F_{ij} = \frac{\alpha_j B_i N_j}{1 + h_j \alpha_j \sum_{i=1}^{nprey}B_i N_j}$ | 313                  |

$F_{ij}$ represents the flux of biomass ($\text{metric tons}/\text{km}²/\text{year}$), $K$ is a parameter representing mean biomass flow ($\text{metric tons}/\text{km}²/\text{year}$), $\alpha$ is the general space clearance rate ($\text{km}²/\text{consumer}/\text{year}$), $\alpha_j$ is the consumer-specific space clearance rate ($\text{km}²/\text{consumer}/\text{year}$), $B_i$ is the prey biomass ($\text{metric tons}/\text{km}²$), $N_j$ is the consumer abundance ($\text{individual}/\text{km}²$) and $h_j$ is the consumer handling time ($\text{metric tons of resource biomass}/\text{km}²/\text{year}$). {#tbl:table_model}

## Model evaluation

All biomass fluxes and body-mass were log-transformed. 
Biomass fluxes were modelled with a hierarchical bayesian approach where $F_{ij}$ follows, after being log-transformed, a normal distribution with mean $\mu$ and standard deviation $\sigma$, where the mean corresponds to the five different models described above respectively. 
Species-specific parameters $\alpha_j$ and $h_j$ were considered as random effects following normal distributions.
As we lacked prior knowledge on potentiel distribution for the parameters, we opted for generic weakly informative priors.
The mean and standard deviation for $\alpha$ and $h_j$ were 0 and 1 respectively and were the same for all models.
The analysis was performed with Stan version 2.32.2 [@StanDevelopmentTeam2024StaMod] via the package rstan in R version 4.3.3 [@RCoreTeam2024LanEnv].

After fitting the data to each model respectively, we used the LOO package [@Vehtari2024LooEff] to compute the expected log pointwise predictive density (ELPD) to perform a leave-one-out (LOO) cross validation based on [@Vehtari2017PraBay] to estimate prediction accuracy.
We computed Pareto diagnostic values per model to evaluate reliability.
Models were ranked by predictive accuracy based on their respective ELPD score.
We also compared the ELPD score between models to evaluate prediction accuracy and their bayesian R² [@Gelman2019RsqBay].
Finally, we tested with linear regression allometric relationships of the space clearance rate parameter $\alpha$ and handling time $h_j$ with consumer body mass.

## Code and data availibility

All the R scripts for model evaluation and figures are available on Github at [https://github.com/BenMerSci/master](https://github.com/BenMerSci/master).

# Results

All models (with the exception of the null hypothesis) had good fit to the data, with $\text{R}^2$ ranging from 0.697 (model 1 - details at @tbl:table_ranking and $\text{R}^2$ posterior distributions in @fig:rsq_plot) to 0.835 (model 3).
The model ranking based on the predictive accuracy with LOO, where higher values are better, revealed that the best performing model is the single species saturating model (model 3) with an ELPD score of -2452.8, almost equal to the multi species saturating model (model 4) and the consumer specific mass action model (model 2) with ELPD scores of -2713.5 and -2749.4 respectively.
The the null model (model 0) and the general mass action model (model 1) followed with ELPD score of -3529.1 and -4056.1, respectively.
Model ranking reveals that, with the exception of model 4, every hypothesis that is added to the model contribute significantly to ELPD and $\text{R}^2$. 
The most significant increases is observed between model 1 and model 2, indicating that, once we account for mass action (model 1), the most important element is predator specific consumption rate (model 2). 
Adding saturation only marginaly improves the fit (model 3), while accounting for multi-species saturation has no significant impact (model 4).  
It is to be noted that both model 3 and model 4 had higher Pareto K diagnostic values (> 0.7), which might indicate non-robust model or highly influential observations [@Vehtari2017PraBay].

| Model   | Expected log pointwise predictive density (ELPD) | $\Delta$ELPD   | Standard error difference | Effective number of parameters (p-LOO) | Number of parameters | mean $\text{R}^2$ |
|---------|--------------------------------------------------|---------|---------------------------|----------------------------------------|----------------------|-------------------|
| model 3 | -2455.4                                          | 0.0     | 0.0                       | 202.5                                  | 313                  | 0.833             |
| model 4 | -2717.7                                          | -262.3  | 28.8                      | 149.5                                  | 313                  | 0.795             |
| model 2 | -2751.3                                          | -295.9  | 30.2                      | 142.2                                  | 157                  | 0.803             |
| model 0 | -3529.1                                          | -1073.7 | 35.7                      | 2.4                                    | 2                    | 0.000             |
| model 1 | -4056.5                                          | -1601.1 | 37.3                      | 2.1                                    | 2                    | 0.696             |

Model ranking based on ELPD with LOO. Models are ranked from best to worst based on their predictive accuracy with the LOO package. {#tbl:table_ranking}

Model comparison suggests that mass action only catches most of the variability in biomass fluxes, but the graphical representation of predicted biomass flows against observed biomass flows reveals a very significant bias that is solved with species-specific space clearance rates (figure @fig:oneone_plot). 
Since the bias in predictions disappears in all three species-specific models and that model 1 ranked below our null model, it was dismissed.
Model ranking and the R² suggest the single species saturating model (model 3) is better than model 2 and 4, but the difference is hardly significant both from statistics (Table @tbl:table_ranking) and graphical representation (figure @fig:oneone_plot).
The consumer specific mass action model (model 2) and the multi-species saturating model (model 4) are the closest together regarding their ELPD score.
Furthermore, the added multi-species aspect of model 4, relative to the single-species model 3, does not improve the fit, neither from statistics nor from graphical representation, therefore dismissing model 4.
The *extreme* Pareto K values of model 3 and 4 would also suggest that both models might not be suited to make prediction as is [@Vehtari2017PraBay].

![Models prediction of biomass fluxes compared to the observed biomass fluxes (log-scale) ($\text{metric tons}/\text{km}^2/\text{year}$). The black line represents a one for one line. Points represent the mean predicted value and thick and fine error bars represent the 0.66 and 0.95 quantile distribution respectively. `Marine and freshwater' points represent biomass fluxes from consumers that are present both in marine and freshwater ecosystems such as Zooplankton and Zoobenthos.](figures/oneone_plots.png){#fig:oneone_plot}

At first glance based on the model ranking and the R², the single species saturating model (model 3) seems to have better predection accuracy than model 2 and 4.
The prediction against observations plots is hinting at the same conclusion, where all three models look pretty similar but the points in model 3 are more grouped around the diagonal line.
The consumer specific mass action model (model 2) and the multi-species saturating model (model 4) are the closest together regarding their ELPD score.
Since model 3 and model 4 are both based on the type II functional response, showing barely no difference in fit and model 3 ranking better, we dismissed model 4.
This decision is also based on parsimony, the extreme Pareto K values and model 2 having a higher R² than model 4.
Posterior distributions of the space clearance rate (figure @fig:alpha_plot) are very similar across the three models, with the distinction that the distribution of model 3 and 4 were wider while model 2 were narrower.
Handling time also varies significantly between species (figure @fig:ht_plot), with some species having very wide distributions and without clear differences between trophic guilds.

![Posterior distribution of the space clearance rate parameter (log-scale) for model 2, 3 and 4.](figures/alpha_comparison.png){#fig:alpha_plot}

![Posterior distribution of the handling time parameter (log-scale) for model 3 and 4.](figures/ht_comparison.png){#fig:ht_plot}

We lastly investigated the relationships between space clearance rate, handling time and body mass.
We found a significant relationship between body masses and the space clearance rate for the specific mass action model (model 2, figure {@fig:allometric_model}.A).
Relationship with the space clearance rate and consumers body mass was significant with a slope of 0.98 (p-value < 0.05, adjusted R² of 0.56).
This relationship was not significant however for space clearance rates extracted from model 3 (model 3, figure @fig:allometric_model .B and @fig:allometric_model .C), neither was the relationship between body mass and handling time.

![Relationships of the space clearance rate and handling time parameters with consumers body mass (log-scale). A clear and discernable relationship is present for model 2 space clearance rate and absent for model 3 space clearance rate and handling time parameters. The allometric relationship for model 2 space clearance rate is also accompanied by a linear regression with a slope of 0.98 (black line) and its 0.95\% confidence interval (grey area). Points represent the mean space clearance rate and thick and fine error bars represent the 0.66 and 0.95 quantile distribution respectively.](figures/model2_3_relationship.png){#fig:allometric_model}

# Discussion

The motivation of this study was to develop predictive models of quantitative interactions for entire food webs.
There are already several techniques to predict the occurrence of interactions and to reconstruct binary interaction networks such as the niche model [@Williams2000SimRul], trait-matching model [@Bartomeus2016ComFra] and machine learning models [@Pichler2020MacLea].
There are also quite a few meta-analyses of functional responses, none of them can be applied to entire food webs as they were mostly based on single species analyses.
Here we developed these one step further with the prediction of biomass flows as a function of mass action, allometric scaling and the full web composition.
To do so, we investigated an ensemble of models to predict biomass flows between populations of consumers and resources inspired from functional response theory.
Four mechanistic model of increasing complexity based on the type I and the type II functional response were compared to test different hypotheses.
In contrast with functional response studies, where the variation of consumption rates of consumers with resource density is evaluated, here we attempted to predict biomass fluxes between all pair of species within a community context.
Upon initial inspection of the fits of each model, it appears that models based upon functional response type I (mass action model) and type II (saturating model) are well suited to predict biomass fluxes.
We discuss hereafter the inherent propreties of each model and compare them regarding their predictive capabilities of biomass fluxes.
Specifically, we compared the different underlying mechanisms and discuss whether mass action is enough or if the incorporation of saturation with consumers handling time is an important addition to predict biomass flows.
We follow by exploring whether the expected allometric relationships with both parameters of interest (space clearance rate and handling time) are observed.
We conclude by addressing the limitations of the study and potentiel next avenues for improving the model.

Overall, based on the Baysian R², the model ranking (table @tbl:table_ranking) and their graphical representation, we found that all the models (except the null model) had a good fit.
While model 1 looks like a good one by looking at the performance metrics, it had a discernable and clear bias in terms of data fitting which undoubtedly arose from the non-specific space clearance rate.
Model 1 portrayed a mass action process where consumption rates simply follows encounters between consumers searching their environment for resources based on a rate at which they clear space [@ODwyer2019EcoIde; @DeLong2021PreEco].
Space clearance rate is expected to vary with species body mass and other traits [@Rall2012UniTem; @DeLong2021PreEco] and our data comprised a variety of organisms ranging from small fish to terrestrial mammals.
The improvement in fit of model 2 in contrast to model 1 further consolidate this hypothesis, where the implementation of a consumer-specific space clearance rate greatly improved model fitting and resulting R², thus dismissing model 1.
With this said, model 2, 3 and 4 all had similar outcomes regarding R² and predictive accuracy (table @tbl:table_ranking), while portraying different ecological mechanisms.
While model 2 implemented a mass action process with consumer-specific space clearance rates, model 3 and 4 incorporated a second mechanism of saturating biomass fluxes with consumers handling time.
Both models 3 and 4 were based upon a type II functional response, where the main difference was that model 3 was saturating biomass fluxes over the biomass of one prey (single-species) while model 4 was accounting for the biomass of all prey species available in the community (multi-species).
While we expect consumers consumption rates over a resource to vary depending on the availability of all its resources of interest [@Smout2010FunRes], the multi-species saturating model underperformed compared to the single-species saturating model.
Accounting for all resource biomass did not seem to improve the fit, thus dismissing model 4.
Given the great diffrence in number of parameters between model 2 and 3 (table @table:table_model), their similar fit, and the high Pareto K values of model 3, model 2 seems to be the most parcimonious choice.
Additionally, there seems to be a tradeoff between the space clearance rate and handling time parameter which introduces variability in the estimation of space clearance rate (figure @fig:alpha_plot).
This tradeoff also seems to impact the expected allometric relationships of space clearance rate and handling time with consumers body mass in model 3 (figure @fig:allometric_model -B-C).
Even though model 3 had the highest R² and ELPD score, it may also suffer from misspecification as indicated by the high Pareto K values [@Vehtari2017PraBay].
While the saturating model might still be relevent and can not totally be dismissed from our analysis, it seems that a simple model such as our consumer-specific mass action model gives a satisfying approximation of biomass fluxes.

## Allometric relationships

The form of the functional response has been the subject of a longstanding debate [@Barbier2021MacApp] since first formalized by @Holling1959ChaSim.
The statistical models we developed operate on a different scale than single species functional response studies, taking advantage of the wide variability of feeding rates among species of different population sizes in a full community, instead of focusing on pairwise interactions with experimental manipulation of a single resource density.
We nonetheless expected to observe similar functional responses and associated parameters since both approach describe the same underlying processes.
Larger organisms are expected to have larger space clearance rate, whereas handling time might vary with consumers and resource body mass [@Rall2012UniTem; @Uiterwaal2020FunRes; @Coblentz2023PreFee; @DeLong2021PreEco}.
Consistent with the anticipated relationship, largest space clearance rate in model 2 are related to larger organisms such as large and medium mammal predators, predatory birds and sharks, while lower space clearance rate are related to smaller organisms such as invertebrates, shrimps and small pelagic fish omnivores (figure @fig:alpha_plot).
The space clearance rate in model 3 mostly displays the same relationship with consumers body mass while having larger flat distributions (figure @fig:alpha_plot).
The allometric relationship with handling time is however less precise, where higher or lower handling time are not specifically related to larger or smaller organisms (figure @fig:alpha_plot)
Based on field observations and modeling, handling time would not be as important in consumptions as resource individuals needed to saturate a consumer's consumption rates could rarely be observed in natural context [@Preston2018WhaDri; @Beardsell2021DerPre; @Coblentz2023PreFee}.
While not necessarily relevant in explaining the poor unobserved body mass relationship of our handling time parameter, it might lend additional support for model 2.
Overall, the inter-consumer distribution of the space clearance rate parameter for model 2 and 3 fall well within the range values reported in other studies [@Rall2012UniTem; @Portalier2022InfSiz; @Coblentz2023PreFee}.

As with many other biological processes, feeding rates are tightly linked with consumers and resources body mass [@Brose2010BodCon; @DeLong2012SizSca; @Schneider2012BodMas; @Schroder2016IndVar; @Preston2018WhaDri; @DeLong2021PreEco].
More specifically, the underlying space clearance rate and handling time parameters of the feeding process are expected to scale with consumer body mass [@Yodzis1992BodSiz; @Vucic-Pestic2010AllFun; @Kalinkat2013BodMas; @DeLong2021PreEco].
A review of several functional response studies summarized in the foRAGE database [@Uiterwaal2022ForDat] showed a clear allometric scaling relationship between consumers body mass and space clearance rate among multiple taxonomic groups [@DeLong2021PreEco].
The allometric scaling of movement speed is hypothesized to be the mechanisms underlying variability in the relationship between consumers body mass and their space clearance rate as it is a function of consumers velocity [@DeLong2021PreEco].
Maximum velocities were shown to be allometrically linked with their body mass, displaying a linear increase on the log-scale up to certain extreme values of body mass [@Bejan2006UniCon; @Hirt2017GenSca].
The estimates of the slope of this relationship however varies significantly between studies, with values that are usually much smaller than 1 [@Rall2012UniTem; @Delong2012DynExpa].
We found an estimated slope of 0.98 on the log-scale (figure @fig:allometric_model -A), with a relatively narrow confidence interval, suggesting a linear relationship between consumer body mass and the space clearance rate, which is coherent with a certain portion of the relationship developed by @Hirt2017GenSca.
Although most of the consumers in model 2 seem to display the expected relationship between space clearance rate and consumers body mass (figure @fig:allometric_model -A), we can clearly discern some species having an upward offset.
The consumers of concern here are all terrestrial carnivores or omnivores belonging to the Arctic networks originating from the same set of study.
As Ecopath compute estimates over a year step [@Christensen2004EcoEco; @Christensen2005EcoEco] and the data from the Arctic networks were seasonally assessed for summer observations, we can not overlook that this offset might arise from a methodological bias.
Alternatively, the higher space clearance rate of these terrestrial species might also arise from other impacting factors such as interaction dimensionality and habitat heterogeneity [@Pawar2012DimCon].
We also note that the allometric relationship disappears with the single-species saturating model (figure @fig:allometric_model -B-C).
We believe this may happen because of a ridge in the likelihood space consequent to a tradeoff between space clearance rate and handling time, making the model non-identifiable.
Perhaps this problem could be solved with stronger priors, for instance using parameters found in traditional functional studies such as @Rall2012UniTem.
Overall, the allometric relationship displayed in the consumer-specific mass action model represents another supporting element in favor of a simple mass-action model, which would significantly facilitates the parameterization of quantitative food web models.

## Quantitative predictions: general extent, scope and limitations

Many techniques were proposed recently to infer ecological interactions from proxies [@Morales-Castilla2015InfBio], some informed by theory [@Portalier2019MecPre], others more flexible and using all of the information contained in the data [@Strydom2021RoaPre].
These methods are motivated by on-going changes in biodiversity [@Jordano2016ChaEco], urging for a more integrated description of community structure.
There is however an inherent challenge in documenting interactions because their number scales with the square of species richness [@MacDonald2020RevLin], some interactions are difficult to document [@Poisot2021GloKno; @Wootton2005MeaInt], and also because novel assemblages are made of species that were never seen co-occurring before [@Montoya2010CliCha; @Lurgi2012NovCom].
The variety of available methods allow some flexibility, depending on the objective of the study and data availability.
They are however all limited to binary interactions, i.e. if a pair of species are interacting or not.
Quantitative information on the strength of interaction is required to move to a next stage of interpretation, just like abundance is a more accurate description of community structure than presence-absence.
We successfully predicted biomass fluxes with a very limited amount of information which suggests that, paired with a method to predict binary interactions, the reconstruction of quantitative interaction networks is accessible.
Our model analysis was inspired by theory, and despite a different methodological approach, our results are in agreement with previous meta-analyses of functional responses [@Uiterwaal2020FunRes; @Rall2012UniTem], further strenghtening the confidence in our models.
We found also coherence in parameter estimates across ecosystems and feeding guilds, suggesting that a general approach is within reach.
Nonetheless, although our models were built upon the best available data at the time, it should not be overlook that our results strongly depend on Ecopath model outputs, and thus their limitations.
As such, the interpretation of our results should reflect this reality.
The obvious next step will be to catch some of the residual variance, likely with the addition of other traits.
Inspired by the methods used for binary interactions, the next model generation will have to account for trait-matching between consumer and ressource.
Interactions could also be made conditional on the environment, for instance on temperature affecting movement rates [@Dell2014TemDep], or the presence of refuges [@Barrios-ONeill2016ConSca; @Chan2017ImpAss].
The parameterization we offered here should eventually contribute to inform theoretical studies [@Schneider2016AniDiv] as well as global ecosystem models that are developed to investigate the consequences of biodiversity changes [@Harfoot2014EmeGlo].

# References
