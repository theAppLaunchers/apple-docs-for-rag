

- App Intents
- ParameterSummaryCaseBuilder
-  buildBlock(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Type Method

# buildBlock(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static func buildBlock(
    _ c0: C0,
    _ c1: C1,
    _ c2: C2,
    _ c3: C3,
    _ c4: C4,
    _ c5: C5,
    _ c6: C6,
    _ c7: C7,
    _ c8: C8,
    _ c9: C9,
    _ c10: C10,
    _ c11: C11,
    _ c12: C12,
    _ default: ParameterSummaryDefaultCaseCondition
) -> ParameterSummaryTupleCaseCondition)> where Intent == C0.Intent, C0 : _ParameterSummarySwitchCase, C1 : _ParameterSummarySwitchCase, C2 : _ParameterSummarySwitchCase, C3 : _ParameterSummarySwitchCase, C4 : _ParameterSummarySwitchCase, C5 : _ParameterSummarySwitchCase, C6 : _ParameterSummarySwitchCase, C7 : _ParameterSummarySwitchCase, C8 : _ParameterSummarySwitchCase, C9 : _ParameterSummarySwitchCase, C10 : _ParameterSummarySwitchCase, C11 : _ParameterSummarySwitchCase, C12 : _ParameterSummarySwitchCase, DefaultSummary : ParameterSummary, C0.Intent == C1.Intent, C1.Intent == C2.Intent, C2.Intent == C3.Intent, C3.Intent == C4.Intent, C4.Intent == C5.Intent, C5.Intent == C6.Intent, C6.Intent == C7.Intent, C7.Intent == C8.Intent, C8.Intent == C9.Intent, C9.Intent == C10.Intent, C10.Intent == C11.Intent, C11.Intent == C12.Intent
```

Available when `Intent` conforms to `AppIntent` and `Value` conforms to `_IntentValue`.

## See Also

### Building switch statement cases

static func buildBlock&lt;C0, DefaultSummary>(C0, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, DefaultSummary>(C0, C1, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, DefaultSummary>(C0, C1, C2, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, DefaultSummary>(C0, C1, C2, C3, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, DefaultSummary>(C0, C1, C2, C3, C4, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, DefaultSummary>(C0, C1, C2, C3, C4, C5, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14, DefaultSummary>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>) -> ParameterSummaryTupleCaseCondition&lt;Intent, Value, (C0, C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14, ParameterSummaryDefaultCaseCondition&lt;Intent, Value, DefaultSummary>)>

struct ParameterSummaryTupleCaseCondition

A type that represents a collection of case conditions for a specific switch statement.

