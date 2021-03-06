# Model training with background jobs

R is often used to build and train machine learning models. Often, this training
process can take a long time, sometimes several hours. In order to remain
productive, it's possible to push model training to the background (either with
local jobs or Launcher jobs) and continue working in the original R session.
This example highlights that workflow.

## Local Background Jobs
When working locally, moving a single job into the background keeps the original
R session free for other work. While multiple jobs can be started concurrently,
training multiple models concurrently with local background jobs can be
computationally expensive, since the jobs are all running on the same machine.
Because if this, it's best to run computationally intensive tasks sequentially
rather than in parallel when using local background jobs.

## Remote Launcher Jobs *(RStudio Server Pro only)*
Using remote background jobs opens up the possibility of running concurrent,
computationally intensive tasks, like training multiple models at once. This is
because Launcher jobs make use of an external resource manager, and jobs can be
distributed so they each have their own independent compute resources. This
workflow can be enhanced by using the Launcher specific funcitons found in the
[`rstudioapi` package](https://github.com/rstudio/rstudioapi).

## Examples

### [Ames](ames)
Example random forest models built using data from the
[`AmesHousing`](https://cran.r-project.org/web/packages/AmesHousing/index.html)
package. The models are built using tools from the
[`tidymodels`](https://github.com/tidymodels) collection of packages and follows
the template outlined
[here](https://tidymodels.github.io/rsample/articles/Applications/Recipes_and_rsample.html).
