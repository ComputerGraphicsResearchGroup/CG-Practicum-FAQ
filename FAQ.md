# Acceleratiedatastructuren

## Hoe een foutieve BVH te debuggen?
Enkele onderdelen die je achtereenvolgens kan testen (aangezien er bugs kunnen voorkomen op redelijk uiteenlopende plaatsen):

Is de afbeelding die je bekomt na renderen zonder BVH correct? 
Is de straal-geometrisch primitief (e.g. straal-driehoek) intersectietest correct geïmplementeerd?

**Invariant**: correct geïmplementeerde straal-driehoek intersectietest


Is de straal-AABB intersectietest correct geïmplementeerd?

**Invariant**: correct geïmplementeerde straal-AABB intersectietest


Indien de volledige BVH doorlopen wordt zonder deze ergens vroegtijdig te verlaten, is de bekomen afbeelding correct? 
(M.a.w. zit alle geometrie ergens in de BVH?)

**Invariant**: correcte geometrie


Zijn de AABBs horende bij elke knoop van de BVH correct?
Indien een BVH top-down geconstrueerd wordt en AABBs top-down berekend worden, 
zijn deze dan exact gelijk aan de AABBs die bottom-up berekend kunnen worden nadat de BVH geconstrueerd is?

**Invariant**: correcte opdeling van de geometrie in de BVH


Berekenen eens een falsecolor afbeelding van ofwel de dichtste intersectiepunten (3 kleurkanalen) ofwel van de straal parameter t-waarden (1 kleurkanaal) (met en zonder BVH)? Kies één pixel (e.g. breakpoints) waarbij de t-waarde met BVH groter is dan zonder BVH, en volg die straal volledig door de boom. Kijk hierbij vooral naar de t-waarden van de linker en rechter AABBs en de beslissingen die hieruit volgen om de boom te doorlopen. Blijkbaar zal er nu ergens een knoop zijn die foutief niet doorlopen wordt en die het dichtstbijzijnde intersectiepunt horende bij de correcte kleinste t-waarde bevat.

**Invariant**: correcte doorloopstrategie van de BVH
