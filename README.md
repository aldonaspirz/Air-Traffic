# Air-Traffic

DESCRIPTION
San Francisco International Airport Report on Monthly Passenger Traffic Statistics by Airline.
SUMMARY
San Francisco International Airport Report on Monthly Passenger Traffic Statistics by Airline. Airport data is seasonal in nature, therefore any comparative analyses should be done on a period-over-period basis (i.e. January 2010 vs. January 2009) as opposed to period-to-period (i.e. January 2010 vs. February 2010). It is also important to note that fact and attribute field relationships are not always 1-to-1. For example, Passenger Counts belonging to United Airlines will appear in multiple attribute fields and are additive, which provides flexibility for the user to derive categorical Passenger Counts as desired.

Source: San Francisco Open Data

https://data.sfgov.org/Transportation/Air-Traffic-Passenger-Statistics/rkru-6vcg

**Celem projektu jest zbudowanie modelu klasyfikacyjnego, który na podstawie podanych danych będzie przewidywał z określoną dokładnością ilu pasażerów zostanie przewiezionych na podstawie podanych parametrów**

* Obróbka danych (Data Processing):
    * Zmieniono nazwy kolumn zgodnie z common practice (nazwy ciągłe bez spacji) - zamieniłam spacje na '_' - funkcja rename
    * Po wstępnym przeglądzie danych (użyte funkcje: info, describe) użyłam pandas_profiling do pogłębionej analizy poszczególnych kolumn - zapisano w pliku 'output.html'
    * Ponieważ dane w kolumnach które należy zanalizować są typu "object" zmieniłam 14 kolumn (wyłączając "Passangers_Count" i "Adjusted_Passangers_Count") za pomocą funkcji factorize na dane liczbowe (float)
    * Zbadałam korelecja poszczególnych kolumn z "Passanger_Count" (funkcja corr)
    * Następnie zwizualizowałam "Passanger_Count" do pozostałych kolumn

* Normalizacja
    * Znormalizowałam kolumny (MinMaxScaler)

* Spilit
    * Podzieliłam dane do modelowania
    Tu pojawił się problem danych typu float -> zmieniłam dane y ("Passanger_Count" na multiclass za pomocą funcji LabelEncoder)

* Klasyfikacja:
   
        * KNeighborsClassifier()
        * GaussianNB()
        * LinearSVC()
        * SGDClassifier()
        * DecisionTreeClassifier()
    
Funkcja którą wykorzystałam do porówniania poszczególnych paramtetrów klasyfikatorów została zaczerpnięta z DataWorkshop realizowanego z Vladimirem Alekseichenko. https://dataworkshop.eu/



