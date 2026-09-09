# Business Insights

Die Analyse des Telecom-Churn-Datensatzes zeigt mehrere Merkmale, die mit einem erhöhten Abwanderungsrisiko verbunden sind.

## 1. Beschwerden als starkes Warnsignal

Kunden mit einer registrierten Beschwerde weisen eine deutlich höhere Churn-Rate auf als Kunden ohne Beschwerde. Auch im Random-Forest-Modell ist das Beschwerdemerkmal das Feature mit der höchsten Feature Importance.

Aus Business-Sicht könnten Beschwerden daher als relevantes Signal genutzt werden, um gefährdete Kunden frühzeitig zu identifizieren und gezielt Retention-Maßnahmen einzuleiten.

## 2. Geringe Nutzung ist mit höherem Churn verbunden

Churn-Kunden zeigen im Durchschnitt eine deutlich geringere Nutzungsintensität.

- Durchschnittliche `Seconds of Use`: 5.014,22 bei Non-Churn gegenüber 1.566,63 bei Churn.
- Durchschnittliche `Frequency of use`: 76,98 bei Non-Churn gegenüber 29,13 bei Churn.
- Durchschnittlicher `Customer Value`: 535,51 bei Non-Churn gegenüber 124,81 bei Churn.

Eine niedrige oder zurückgehende Kundenaktivität könnte daher ein relevantes Frühwarnsignal für Abwanderung darstellen.

## 3. Kundenstatus ist relevant

Nicht-aktive Kunden weisen eine deutlich höhere Churn-Rate auf als aktive Kunden. Der nicht-aktive Status gehört ebenfalls zu den wichtigsten Merkmalen des Random Forest.

Eine Kombination aus geringer Aktivität und nicht-aktivem Kundenstatus könnte deshalb für die Priorisierung von Retention-Maßnahmen interessant sein.

## 4. Tarifmodelle unterscheiden sich

Kunden im Pay-as-you-go-Tarif weisen im untersuchten Datensatz eine deutlich höhere Churn-Rate auf als Kunden mit vertraglichem Tarif.

Im Random Forest besitzt der Tarifplan jedoch nur eine geringe zusätzliche Feature Importance. Dies zeigt, dass ein Merkmal isoliert mit Churn zusammenhängen kann, im Zusammenspiel mit anderen Variablen aber wenig zusätzliche Vorhersageinformation liefern muss.

## 5. Niedrige Charge-Amount-Stufen sind auffällig

Bei `Charge Amount = 0` liegt die Churn-Rate bei 23,81 %. Von den insgesamt 495 Churn-Fällen im ursprünglichen Datensatz entfallen 421 auf diese Gruppe.

Mit steigender Charge-Amount-Stufe sinkt die beobachtete Churn-Rate deutlich. Höhere Stufen enthalten jedoch teilweise nur wenige Beobachtungen und müssen deshalb vorsichtig interpretiert werden.

## Modellbasierte Erkenntnis

Von den beiden untersuchten Modellen erzielt der Random Forest die stärkere Testperformance:

- Accuracy: 96,1 %
- Precision: 93,5 %
- Recall: 80,9 %
- F1-Score: 0,867
- ROC-AUC: 0,985

Besonders relevant für den Churn-Anwendungsfall ist der Recall. Der Random Forest erkennt 72 von 89 tatsächlichen Churn-Fällen, während die Logistic Regression nur 42 erkennt.

## Einschränkungen

Die Ergebnisse beschreiben Zusammenhänge innerhalb des verwendeten Datensatzes und erlauben keine kausalen Schlussfolgerungen.

Der Datensatz enthält außerdem keine eindeutige Kunden-ID. Identische Merkmalsprofile können daher nicht zweifelsfrei einzelnen Kunden zugeordnet werden. Zusätzlich bestehen starke Korrelationen zwischen mehreren Nutzungsmerkmalen.

Der Random Forest zeigt eine gewisse Overfitting-Tendenz, da seine Trainingsperformance nahezu perfekt ist. Für eine weiterführende Analyse wären Cross-Validation, Hyperparameter-Tuning und die Validierung auf zusätzlichen bzw. aktuelleren Telecom-Daten sinnvoll.