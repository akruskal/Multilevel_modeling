# HDAT9700 Term3 2019 Assessment 1c

## Feedback
Good work overall Alex. Your code is generally correct, but in a few places it seemed like you either didn't quite answer the question that was asked (e.g. Q4v) or didn't pick up on mistakes because you didn't interrogate the output (e.g. Q5ii - iv). Make sure to give yourself plenty of time to pay attention to the detail for the final assignment! Keep up the good work. 


## Marks

| Question  | Mark            | Comment        |
  |---------------------------|----------------|----------------|
  | 1(i)      | 3/3            | 	             |
  | 1(ii)     | 3/3            |                | 
  | 2(i)     	| 1/3            |   To describe sex as a level in the multilevel structure is to assume the effect on the outcome can be modelled as a random effect. It makes mores sense to model sex as a fixed effect. I would describe the multilevel structure here as a two-level hierarchy with observations (level 1) nested within individuals (level 2).             |
  | 2(ii)   	| 1/5            | You say that "If we considered age a fixed effect, we would not be able to see the difference in size by age". That is not quite the case, you would see the difference in size by age _on average_. A key point is that the relationship between age and distance may plausibly vary across individuals. Modelling age as a random effect allows you to model that variation.                |
  | 2(iii)   	| 3/3            |                |
  | 3(i)     	| 3/3            |                |
  | 3(ii)    	| 3/3            |                |
  | 3(iii)   	| 1/3            | You calculated the loglikelihood for both models, but you didn't carry out the test or comment on the difference to argue that a test wasn't neccessary.               |
  | 3(iv)   	| 3/3            |                |
  | 3(v)     	| 3/3            |                |
  | 4(i)     	| 3/3            |                |
  | 4(ii)     | 3/3            |                |
  | 4(iii)   	| 3/3            |                |
  | 4(iv)   	| 4/6            | You suggest that "as people age, the distance between the fissures become less varied". I see where you are coming from because the "fanning in" picture results in the individual lines drawing closer together over time. But, depending on the coding of the random effect, it is not generally true that a negative covariance will imply less variation as the exposire increases. Imagine that the lines fanning in together start to cross over and fan out. A simpler interpretation for the negative covariance is that individuals with an above average random intercept will have a below average random slope, and those with a below average random intercept will have an above average random slope.               |
  | 4(v)     	| 0/6            | You have plotted the observed data, whereas the question asked you to plot the posterior estimates of the random intercepts and random slopes. These are the estimated departures from the grand intercept ($u_{0j}$) and the grand slope ($u_{1j}$). Remember in the model we don't estimate these directly, instead we estimate their variance. But we can get posterior (post-estimation) estimates of $u_{0j}$ and $u_{1j}$  using the function `ranef()`. Nice plots though! As an aside, it is aways good to add a line or two of commentary about any plots you produce.            |
  | 4(vi)    	| 3/3            |                |
  | 5(i)     	| 3/3            |                |
  | 5(ii)     | 0/3            | The syntax to add the quadratic term is incorrect, i.e. you can't use `age + age^2` you must use `age + I(age^2)` or create a new variable equal to the square of age and add that. If you call `summary()` on the model object you created there is no squared term in the model output. Lost marks not so much for the error in syntax, which is minor, but for failing to examine the output and recognising that the model wasn't fitting what you had intended.   |
  | 5(iii)   	| 0/3            | The code is correct but the output doesn't make sense. There is no test performed because the two models are the same.  |
  | 5(iv)   	| 0/3            | Tecnically you are right but you couldn't have ascertained that as you didn't fit the model.               |
  | 6(i)     	| 3/3            | I won't deduct marks again for the the same mistake, but the same comment applies as above.                |
  | 6(ii)     | 3/3            |                 |
  | 6(iii)   	| 5/6            | Generally good answer, but one nuance - you comment that the curves are different, with "female looking more linear and males looking non-linear", but note that the interaction term added in this model assumes a linear association for boys and girls. The interaction means you fit two straight lines, not curves.  |
  | 7       	| 10/20           | When summarising results you would usually provide and interpret the point estiamte with 95% CIs rather than just the CIs as you have done. It is better to refer to the variable concept rather than the variable name as coded in the software, especially if the latter is not very meaningful (i.e. refer to the parameter estimates for 'girls' not 'SexFemale'). You have to take care when interpreting parameter estimates in the presence of interactions. For example, in the final model, the parameter for age (0.63) is specific to boys; the corresponding parameter for girls would be the main effect of age plus the interaction term (0.63 - 0.54). Another complication in the presence of interactions is that the main effect for girls is the difference between boys and girls **when age is zero**. Because this is way outside the range of ages in the observed data, it is tricky to present this. One way around this would be to use the model estimates to calculate the difference at more relevant age. An alternative is to recode the age variable (see my solutions).   |
  | Total     | 64/100          | Good work Alex               |
  | Total with late penalty | 61/100 | |
  