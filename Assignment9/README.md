**What performed better the random forest or the decision tree?**

**The Random Forest performed better overall**

**Accuracy:**
- Random Forest: **85%**
-  Decision Tree: **72%**
-  → Random Forest wins
   
**However, for predicting loan defaulters (class 1 = not fully paid):**
- Decision Tree recall: **0.20** (caught 20% of defaulters)
- Random Forest recall: **0.01** (caught only 1% of defaulters)
- → Decision Tree actually wins here

**The core trade-off:**

Metric                 | Decision Tree | Random Forest |

Overall Accuracy       | 72%           | 85%           |

Class 0 (paid) F1      | 0.83          | 0.92          |

Class 1 (defaulted) F1 | 0.18          | 0.02          |

Defaulters caught      | 88/443        | 5/443         |


**Conclusion:** 

The Random Forest is better at the overall accuracy score, but it almost completely ignores the minority class, predicting nearly everyone as "fully paid." 

The Decision Tree is more balanced and actually catches some defaulters, which is arguably more valuable in a real lending scenario — since missing a defaulter is more costly than missing a good borrower.
