# Accessibility Evaluation Report for WCAG 2.2

## 1. Executive Summary
This report describes the conformance of the Hornbill Collaboration Core and its applications with W3C's Web Content Accessibility Guidelines (WCAG) 2.2. The Success Criteria (checklist) is described in Section 4 below and is based on the Success Criteria checklist provided by W3C ( https://www.w3.org/WAI/WCAG22/implementation-report/ )

## 2. Last Reviewed
http://live.hornbill.com/INSTANCE_NAME/  
Using Preview UI - English  
22-02-2024  
By _Daniel Dekel_ - Principal Web Developer - Hornbill Technologies Limited

## 3. Review Process
* WCAG 2.2 Level 1 (A), Level 2 (AA) and Level 3 (AAA)
* Used HTMLHint (http://htmlhint.com/) to validate the HTML Content of all our source code
* Used W3C Checklist and Overview https://webaim.org/standards/wcag/checklist and https://www.w3.org/WAI/WCAG22/quickref/?versions=2.2
* https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/
* Made a manual review to our source code and our run-time environment

## 4. Commitment to Accessibility Improvements
We have not fully met every point in the requirements so far. Some of the unaddressed points are subjective, and we don't fully understand the application of them in all cases, leaving it difficult for us to make meaningful changes that will serve people with impaired sight issues without degrading the product for them or for anyone else.  
<br>
To that end, we have taken the view that rather than trying to meet every point just for the sake of ticking the boxes, the more subjective/ambiguous points have not been addressed because we do not have enough of an understanding about how we might address the issues without degrading the function of Hornbill's products.  
<br>
We recognize that we do not understand how these unaddressed issues might be applied in a practical sense, and so want to tackle the remaining issues as and when there are practical examples we can work with. We remain both committed and open-minded about these items and will address them, but are hoping to work with customers on individual requirements and individual user needs as required.

## 5. Summary and Recommended Actions

### Overall
There are 85 checks in total. 67 are fully met. 6 are partially met, 6 are not and 6 are not applicable.

### Results for Level 1 (A)
There are 30 checks in total for Level 1  

30 are fully met.

### Results for Level 2 (AA)
There are 24 checks in total for Level 2  

21 are fully met. 1 is not met and 2 are not applicable.

### Results for Level 3 (AAA)
There are 31 checks in total for Level 3  

16 are fully met. 6 are partially met, 5 are not met and 4 are not applicable.

### General
Items that are not met - Explanation
| Guideline | Description | Level | Result | Explanation |
|--|--|:--:|:--:|--|
| 2.2.5     | Re-authenticating             | AAA   | <span class="text-danger">Not met</span> | When the session expires there is no way to continue working without leaving the page and re-authenticating |
| 2.2.6     | Timeouts _(Added in 2.1)_       | AAA   | <span class="text-danger">Not met</span> | There is no warning about data loss when the session is about to expire |
| 2.5.5     | Target Size (Enhanced) _(Added in 2.1)_         | AAA   | <span class="text-danger">Not met</span> | Some target elements are smaller than 44 pixels |
| 2.5.7     | Dragging Movements _(Added in 2.2)_             | AA    | <span class="text-danger">Not met</span> | In some areas, drag and drop requires a mouse device. |
| 3.1.5     | Reading Level                     | AAA   | <span class="text-danger">Not met</span> | There is no alternative text for lower education level. This might not be applicable for this type of product |
| 3.1.6     | Pronunciation                     | AAA   | <span class="text-danger">Not met</span> | There is no mechanism to identify specific pronunciation |

## Checklist
### Principle 1 – Perceivable
#### Guideline 1.1 - Text Alternatives
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 1.1.1     | Non-text Content      | A     | <span class="text-success">Fully Met</span> |

#### Guideline 1.2 – Time-based Media
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 1.2.2     | Audio-only and Video-only (Prerecorded) | A     | <span class="text-success">Fully Met</span> |
| 1.2.3     | Audio Description or Media Alternative (Prerecorded) | A     | <span class="text-success">Fully Met</span> |
| 1.2.4     | Captions (Live)                   | AA    | <span class="text-secondary">N/A</span> |
| 1.2.5     | Audio Description (Prerecorded)   | AA    | <span class="text-secondary">N/A</span> |
| 1.2.6     | Sign Language (Prerecorded)       | AAA   | <span class="text-secondary">N/A</span> |
| 1.2.7     | Extended Audio Description (Prerecorded) | AAA   | <span class="text-secondary">N/A</span> |
| 1.2.8     | Media Alternative (Prerecorded)   | AAA   | <span class="text-secondary">N/A</span> |
| 1.2.9     | Audio-only (Live)                 | AAA   | <span class="text-secondary">N/A</span> |

#### Guideline 1.3 - Adaptable
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 1.3.1     | Info and Relationships        | A     | <span class="text-success">Fully Met</span> |
| 1.3.2     | Meaningful Sequence           | A     | <span class="text-success">Fully Met</span> |
| 1.3.3     | Sensory Characteristics       | A     | <span class="text-success">Fully Met</span> |
| 1.3.4     | Orientation _(Added in 2.1)_            | AA    | <span class="text-success">Fully Met</span> |
| 1.3.5     | Identify Input Purpose _(Added in 2.1)_ | AA    | <span class="text-success">Fully Met</span> |
| 1.3.6     | Identify Purpose _(Added in 2.1)_       | AAA   | <span class="text-success">Fully Met</span> |

#### Guideline 1.4 - Distinguishable
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 1.4.1     | Use of Color                  | A     | <span class="text-success">Fully Met</span> |
| 1.4.2     | Audio Control                 | A     | <span class="text-success">Fully Met</span> |
| 1.4.3     | Contrast (Minimum)            | AA    | <span class="text-success">Fully Met</span> |
| 1.4.4     | Resize Text                   | AA    | <span class="text-success">Fully Met</span> |
| 1.4.5     | Images of Text                | AA    | <span class="text-success">Fully Met</span> |
| 1.4.6     | Contrast (Enhanced)           | AAA   | <span class="text-success">Fully Met</span> |
| 1.4.7     | Low or No Background Audio    | AAA   | <span class="text-success">Fully Met</span> |
| 1.4.8     | Visual Presentation           | AAA   | <span class="text-success">Fully Met</span> |
| 1.4.9     | Images of Text (No Exception) | AAA   | <span class="text-success">Fully Met</span> |
| 1.4.10    | Reflow _(Added in 2.1)_             | AA    | <span class="text-success">Fully Met</span> |
| 1.4.11    | Non-text Contrast _(Added in 2.1)_  | AA    | <span class="text-success">Fully Met</span> |
| 1.4.12    | Text Spacing _(Added in 2.1)_       | AA    | <span class="text-success">Fully Met</span> |
| 1.4.13    | Content on Hover or Focus _(Added in 2.1)_ | AA    | <span class="text-success">Fully Met</span> |

### Principle 2 – Operable
#### Guideline 2.1 – Keyboard Accessible
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 2.1.1     | Keyboard                      | A     | <span class="text-success">Fully Met</span> |
| 2.1.2     | No Keyboard Trap              | A     | <span class="text-success">Fully Met</span> |
| 2.1.3     | Keyboard (No Exception)       | AAA   | <span class="text-warning">Partially Met</span> |
| 2.1.4     | Character Key Shortcuts _(Added in 2.1)_ | A     | <span class="text-success">Fully Met</span> |

#### Guideline 2.2 – Enough Time
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 2.2.1     | Timing Adjustable             | A     | <span class="text-success">Fully Met</span> |
| 2.2.2     | Pause, Stop, Hide             | A     | <span class="text-success">Fully Met</span> |
| 2.2.3     | No Timing                     | AAA   | <span class="text-success">Fully Met</span> |
| 2.2.4     | Interruptions                 | AAA   | <span class="text-warning">Partially Met</span> |
| 2.2.5     | Re-authenticating             | AAA   | <span class="text-danger">Not met</span> |
| 2.2.6     | Timeouts _(Added in 2.1)_       | AAA   | <span class="text-danger">Not met</span> |

#### Guideline 2.3 – Seizures and Physical Reactions
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 2.3.1     | Three Flashes or Below Threshold  | A     | <span class="text-success">Fully Met</span> |
| 2.3.2     | Three Flashes                     | AAA   | <span class="text-success">Fully Met</span> |
| 2.3.3     | Animation from Interactions _(Added in 2.1)_ | AAA   | <span class="text-warning">Partially Met</span> |

#### Guideline 2.4 – Navigable
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 2.4.1     | Bypass Blocks                     | A     | <span class="text-success">Fully Met</span> |
| 2.4.2     | Page Titled                       | A     | <span class="text-success">Fully Met</span> |
| 2.4.3     | Focus Order                       | A     | <span class="text-success">Fully Met</span> |
| 2.4.4     | Link Purpose (In Context)         | A     | <span class="text-success">Fully Met</span> |
| 2.4.5     | Multiple Ways                     | AA    | <span class="text-success">Fully Met</span> |
| 2.4.6     | Headings and Labels               | AA    | <span class="text-success">Fully Met</span> |
| 2.4.7     | Focus Visible                     | AA    | <span class="text-success">Fully Met</span> |
| 2.4.8     | Location                          | AAA   | <span class="text-success">Fully Met</span> |
| 2.4.9     | Link Purpose (Link Only)          | AAA   | <span class="text-warning">Partially Met</span> |
| 2.4.10    | Section Headings                  | AAA   | <span class="text-success">Fully Met</span> |
| 2.4.12    | Focus Not Obscured (Minimum) _(Added in 2.2)_   | AA    | <span class="text-success">Fully Met</span> |
| 2.4.13    | Focus Not Obscured (Enhanced) _(Added in 2.2)_  | AAA   | <span class="text-success">Fully Met</span> |
| 2.4.13    | Focus Appearance _(Added in 2.2)_   | AAA   | <span class="text-warning">Partially Met</span> |

#### Guideline 2.5 – Input Modalities
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 2.5.1     | Pointer Gestures _(Added in 2.1)_               | A     | <span class="text-success">Fully Met</span> |
| 2.5.2     | Pointer Cancelation _(Added in 2.1)_            | A     | <span class="text-success">Fully Met</span> |
| 2.5.3     | Label in Name _(Added in 2.1)_                  | A     | <span class="text-success">Fully Met</span> |
| 2.5.4     | Motion Actuation _(Added in 2.1)_               | A     | <span class="text-success">Fully Met</span> |
| 2.5.5     | Target Size (Enhanced) _(Added in 2.1)_         | AAA   | <span class="text-danger">Not met</span> |
| 2.5.6     | Concurrent Input Mechanisms _(Added in 2.1)_    | AAA   | <span class="text-success">Fully Met</span> |
| 2.5.7     | Dragging Movements _(Added in 2.2)_             | AA    | <span class="text-danger">Not met</span> |
| 2.5.8     | Target Size (Minimum) _(Added in 2.2)_          | AA    | <span class="text-success">Fully Met</span> |

### Principle 3 – Understandable
#### Guideline 3.1 – Readable
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 3.1.1     | Language of Page                  | A     | <span class="text-success">Fully Met</span> |
| 3.1.2     | Language of Parts                 | AA    | <span class="text-success">Fully Met</span> |
| 3.1.3     | Unusual Words                     | AAA   | <span class="text-warning">Partially Met</span> |
| 3.1.4     | Abbreviations                     | AAA   | <span class="text-success">Fully Met</span> |
| 3.1.5     | Reading Level                     | AAA   | <span class="text-danger">Not met</span> |
| 3.1.6     | Pronunciation                     | AAA   | <span class="text-danger">Not met</span> |

#### Guideline 3.2 – Predictable
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 3.2.1     | On Focus                          | A     | <span class="text-success">Fully Met</span> |
| 3.2.2     | On Input                          | A     | <span class="text-success">Fully Met</span> |
| 3.2.3     | Consistent Navigation             | AA    | <span class="text-success">Fully Met</span> |
| 3.2.4     | Consistent Identification         | AA    | <span class="text-success">Fully Met</span> |
| 3.2.5     | Change on Request                 | AAA   | <span class="text-success">Fully Met</span>  |
| 3.2.6     | Consistent Help _(Added in 2.2)_  | A     | <span class="text-success">Fully Met</span> |

#### Guideline 3.3 – Input Assistance
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 3.3.1     | Error Identification              | A     | <span class="text-success">Fully Met</span> |
| 3.3.2     | Labels or Instructions            | A     | <span class="text-success">Fully Met</span> |
| 3.3.3     | Error Suggestion                  | AA    | <span class="text-success">Fully Met</span> |
| 3.3.4     | Error Prevention (Legal, Financial, Data) | AA    | <span class="text-success">Fully Met</span> |
| 3.3.5     | Help                              | AAA   | <span class="text-success">Fully Met</span> |
| 3.3.6     | Error Prevention (All)            | AAA   | <span class="text-success">Fully Met</span>  |
| 3.3.7     | Redundant Entry _(Added in 2.2)_    | A     | <span class="text-success">Fully Met</span> |
| 3.3.8     | Accessible Authentication (Minimum) _(Added in 2.2)_    | AA    | <span class="text-success">Fully Met</span> |
| 3.3.9     | Accessible Authentication (Enhanced) _(Added in 2.2)_   | AAA   | <span class="text-success">Fully Met</span> |

### Principle 4 – Robust
#### Guideline 4.1 – Compatible
| Guideline | Description | Level | Result |
|--|--|:--:|:--:|
| 4.1.2     | Name, Role, Value                 | A     | <span class="text-success">Fully Met</span> |
| 4.1.3     | Status Messages _(Added in 2.1)_    | AA    | <span class="text-success">Fully Met</span> |

## Additional Resources:
1. https://webaim.org/standards/wcag/checklist 
2. https://www.w3.org/WAI/WCAG22/quickref/?versions=2.2
