- Evaluations  
- Evaluations  
  
Framework  
  
# Evaluations  
  
Measure the quality of your app’s intelligence-powered features.  
  
macOS 27.0+  
  
## Overview  
  
Use the Evaluations framework to systematically evaluate your app’s intelligence-powered features. Define datasets, generate model responses, apply metrics, and aggregate results, all with type-safe Swift APIs that integrate directly into your development workflow.  
  
With the Evaluations framework, you can:  
  
- Compare prompt strategies.  
- Track quality over time.  
- Catch regressions before they ship.  
  
The framework evaluates your intelligence-powered features against the metrics you define, from simple pass or fail checks to detailed scoring with model-as-judge patterns. It aggregates the results into summaries that show you which approach performs best and where individual responses fall short. The framework works with any model available through Foundation Models, including on-device, Private Cloud Compute, and other models.  
  
## Topics  
  
### Essentials  
  
Evaluating language model responses  
  
Build an evaluation that runs your intelligence-powered feature against samples and scores each response.  
  
Designing effective evaluations  
  
Design evaluations that tell you how well your feature works, why it fails, and where to focus next.  
  
Book Tracker: Using Evaluations to evaluate an intelligent feature  
  
Measure and improve the quality of your app’s intelligence-powered features using the Evaluations framework.  
  
protocol Evaluation  
  
A type that defines an evaluation.  
  
### Datasets  
  
Generating synthetic datasets  
  
Expand a small set of manually written evaluation samples into a larger dataset.  
  
Designing datasets to test your feature  
  
Build categorized test datasets that reflect the full range of real-world use of your feature.  
  
struct ModelSample  
  
A general-purpose language model evaluation sample.  
  
protocol Loader  
  
A protocol for types that supply a dataset for evaluation.  
  
actor SampleGenerator  
  
An actor that generates evaluation samples using a language model.  
  
### Metrics and evaluators  
  
Designing specific, measurable criteria in an evaluation suite  
  
Define quality for your feature by choosing measurable criteria, scoring approaches, and ground-truth strategies.  
  
struct Metric  
  
A named metric that carries a result value.  
  
struct Evaluator  
  
A closure-based evaluator.  
  
struct MetricsAggregator  
  
A utility for computing aggregate statistics from evaluation metrics.  
  
### Results  
  
struct EvaluationResult  
  
The results of running a model evaluation.  
  
struct ResultColumn  
  
A typed descriptor for a column in an evaluation result DataFrame.  
  
var inputColumn: ResultColumn<Self.Sample>  
  
A typed column descriptor for the input samples in the detailed DataFrame.  
  
var responseColumn: ResultColumn<Self.Subject>  
  
A typed column descriptor for the model responses in the detailed DataFrame.  
var expectedColumn: ResultColumn<Self.Sample.ExpectedValue>  
A typed column descriptor for the expected values in the detailed DataFrame.  
  
### Model-as-judge evaluations  
  
Designing effective model-as-judge evaluators  
  
Configure model-as-judge evaluators that produce scores you correlate with human review.  
  
Scoring with model-as-judge evaluators  
  
Score subjective qualities like tone, accuracy, and relevance that programmatic checks cannot measure.  
  
struct ModelJudgeEvaluator  
  
An evaluator that uses a language model as a judge to score responses.  
  
struct ModelJudgePrompt  
  
A configuration for how a model-as-judge evaluator constructs its prompt.  
  
struct ScoreDimension  
  
A named scoring dimension for a model judge evaluator.  
  
### Tool-call evaluation  
  
Evaluating tool-calling behavior  
  
Analyze your model’s tool calls against expected trajectories, argument values, and call ordering.  
  
struct ToolCallEvaluator  
  
An evaluator that verifies agentic tool calls against an expected trajectory.  
  
struct TrajectoryExpectation  
  
The expected pattern of tool calls for an evaluation.  
  
enum ArgumentMatcher  
  
The values that define how to validate a tool-call argument.  
  
### Swift Testing integration  
  
struct EvaluationTrait  
  
A test trait that runs an evaluation and records the result as attachments.  
  
struct EvaluationContext  
  
A context that provides the evaluation result within a test scope.  
