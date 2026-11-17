- TrustInsights  
- Trust Insights  
  
Framework  
  
# Trust Insights  
  
Evaluate transactions for potential coercive activity while preserving people’s privacy.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+  
  
## Overview  
  
The Trust Insights framework enables your app to request an evaluation, or insight, to help detect and respond to social engineering threats people may face. Social threats exploit human psychology rather than technical vulnerabilities such as software bugs to pressure or deceive people into performing legitimate actions, and your app can’t distinguish between a genuine or a coerced interaction.  
  
## Learn about available action contexts  
  
There are five principal action areas — kinds of transactions people might engage in — that the Trust Insights framework can help evaluate:  
  
InsightEvaluator.OperationCategory.payment  
  
An action that indicates some form of payment or purchase.  
  
InsightEvaluator.OperationCategory.account  
  
An action that indicates an account operation including registration, login, or the modification of account details.  
  
InsightEvaluator.OperationCategory.resourceUse  
  
An action that indicates usage of some resource, such as an expensive computation capability or online service.  
  
InsightEvaluator.OperationCategory.communication  
  
An action that indicates communication operation, such as sending bulk messages or making connections to other people.  
  
InsightEvaluator.OperationCategory.other  
  
A default action that represents all other types of actions. If the available action types aren’t appropriate for your use case, please consider filing a Feedback report with the details relating to the category of interest.  
  
## Enable your Xcode project to adopt the Trust Insights framework  
  
The Trust Insights framework requires that your app’s Xcode project enables the com.apple.developer.trustinsights.base entitlement. For information on how to add this entitlement to your Xcode project, see Trust Insights.  
  
## Understand the components of trust evaluation request  
  
A trust insight is the result of two elements that combine to form a trust insight evaluation request.  
  
request  
  
A trust insight request that represents a specific signal or insight. The framework supports one type of request, IsLikelyBeingCoachedInsight.  
  
context  
  
A context that describes what kind of action someone is attempting to perform. For a complete list of actions, see Learn about available action contexts  
  
## Create an evaluator and request an evaluation  
  
In order to request evaluations, you need to first request a person’s permission to use the Trust Insights framework. The following example demonstrates how to check your app’s authorization status and request a person’s authorization, provided a person hasn’t previously declined an authorization request.  
  
``` swift  
    /// Returns `true` if a person has authorized use of Trust Insights,  otherwise `false`.  
    func requestUserAuthorizationIfNeeded(context: InsightEvaluator.InsightContext) async -> Bool{  
        do {  
            let evaluator = InsightEvaluator()  
            switch try await evaluator.authorizationStatus(for: context) {  
            case .authorized:  
                return true  
            case .notDetermined, .deniedRequestable:  
                // Present a screen that explains the benefits of opting into trust insights   
                // (called  `try presentAppInformationScreen()` in this example) that presents   
                // an option to allow use of the framework.  
                let updateAuthStatus = try await evaluator.requestAuthorization(for: context)  
                return updateAuthStatus == .authorized  
            case .unavailable, .denied:  
                return false  
            @unknown default:  
                return false  
            }  
        } catch {  
            return false  
        }  
    }  
```  
  
## Act on the result of the evaluation  
  
The result of a Trust Insight evaluation can help you determine if you should perform further checks before finalizing a transaction. The following example shows a function that returns a Boolean value indicating whether the framework indicates there are no indications of coaching.  
  
``` swift  
func shouldBypassCheckX() async -> Bool {  
    do {  
        let requestedAssessment = IsLikelyBeingCoachedInsight.request(schema: .version1)  
        let context = InsightEvaluator.InsightContext(  
            operationCategory: .communication,  
            requestedEvaluations: requestedAssessment)  
        guard await requestUserAuthorizationIfNeeded(context: context) else { return false }  
        let evaluator = InsightEvaluator()  
        let evaluation = try await evaluator.requestEvaluation(context: context)  
        switch try evaluation.insight.outcome.get() {  
        case .unknown:  
            evaluation.reportConsumption(.usedReducedFriction)  
            return true  
        case .medium, .high:  
            evaluation.reportConsumption(.usedIncreasedFriction)  
            return false  
        default:  
            evaluation.reportConsumption(.notUsedError)  
            return false  
        }  
    } catch {  
        return false  
    }  
}  
```  
  
## Topics  
  
### Obtaining permission or checking authorization to perform evaluations  
  
func requestAuthorization<each I>(for: InsightEvaluator.InsightContext<repeat each I>) async throws -> InsightEvaluator.AuthorizationStatus  
  
Requests authorization from a person to generate evaluations.  
  
func authorizationStatus<each I>(for: InsightEvaluator.InsightContext<repeat each I>) async throws -> InsightEvaluator.AuthorizationStatus  
  
Returns an authorization status that indicates whether a person permitted the app to request evaluations for the given context.  
  
enum AuthorizationStatus  
  
Values that indicate the status of the app’s authorization to request evaluations.  
  
### Creating an insight evaluation  
  
init()  
  
Creates a new insight evaluator object you use to request insights.  
  
### Requesting an evaluation  
  
class InsightEvaluator  
  
A class that defines data and methods the framework uses to perform evaluations.  
  
func requestEvaluation<each I>(context: InsightEvaluator.InsightContext<repeat each I>) async throws -> InsightEvaluation<repeat (each I).InsightType>  
  
Requests the evaluation of insights.  
  
class InsightEvaluation  
  
The insight result that an evaluation request returns.  
  
protocol TrustInsight  
  
A protocol that describes the trust insight model and the associated evaluation properties.  
  
### Evaluating insight signals  
  
struct IsLikelyBeingCoachedInsight  
  
An insight to request to examine indications that someone may be actively coaching a person to perform actions.  
  
### Receiving evaluation notifications and handling errors  
  
enum InsightEvaluationConsumptionStatus  
  
Values describing the usage of insight evaluation.  
  
enum InsightError  
  
Error values the framework returns for specific insights within the overall evaluation.  
  
### Providing feedback  
  
func reportConsumption(InsightEvaluationConsumptionStatus, insightIDsUsed: [String])  
  
Reports the consumption status, and optionally provides one or more associated insight identifiers.  
  
func reportConsumption(InsightEvaluationConsumptionStatus, insightsUsed: [any TrustInsight])  
  
Reports the consumption status, and optionally provide one or more associated insights.  
