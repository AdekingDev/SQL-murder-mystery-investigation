# SQL-murder-mystery-investigation
Solved a fictional homicide using pure SQL.. chained joins, filters, and aggregation across 8 relational tables to identify both the hitman and the mastermind who hired him. Includes full query log, findings report, and reproducible investigation walkthrough.

## The Incident

On January 15, 2018, a murder was reported in SQL City. The original crime scene report had been lost, so the entire case had to be reconstructed from the police department's raw relational database.. nine interconnected tables, no pre-built answer key, no shortcuts.

Querying the crime scene records surfaced the starting thread: security footage placed two witnesses at the scene. One lived in the last house on Northwestern Drive; the other, a woman named Annabel, lived somewhere on Franklin Avenue.

## Finding the Witnesses

Neither witness had a full address on record, just a street name and a loose descriptor ("last house," "named Annabel"). Filtering and sorting the person table by house number resolved witness #1 to Morty Schapiro at 4919 Northwestern Dr. A simple name-pattern match on Franklin Avenue resolved witness #2 to Annabel Miller.

## The Testimony

Their interview transcripts contained the real evidence:

Morty heard a gunshot and saw a man flee carrying a "Get Fit Now Gym" bag — gold-member only, with a membership number starting "48Z" and get into a car with a plate containing "H42W."
Annabel recognized the killer from her own gym, where she'd seen him working out on January 9th.

These weren't full identifiers, they were fragments. The investigation had to treat each fragment as a filter and stack them until only one person survived every pass.

## Isolating the Suspect

Filtering gym membership records for gold members with an ID starting "48Z" returned two names: Joe Germuska and Jeremy Bowers. Both had, in fact, checked into the gym on January 9th.. the fragment alone wasn't enough to separate them. The license plate was the deciding filter: joining membership records to driver's license data showed only one of the two owned a vehicle with a plate matching "H42W" a Chevrolet Spark LS, plate 0H42W2.

## Suspect identified: Jeremy Bowers.

## The Twist — A Hired Hand

Standard investigative discipline says never close a case on the first name that fits, so Bowers' own interview was pulled before the file was closed. It changed the entire shape of the case: Bowers stated he'd been hired by a woman with significant money.. 5'5" to 5'7", red hair, driving a Tesla Model S, who had attended the SQL Symphony Concert three times in December 2017.

## Unmasking the Mastermind

Cross-referencing driver's license records against that physical description and vehicle produced three matches, a false sense of closure, since three people fit the same profile. The tie-breaker was behavioral, not physical: pulling Facebook event check-in records and counting December attendances at the SQL Symphony Concert isolated exactly one person who attended all three times.

## Mastermind identified: Miranda Priestly.

## Corroborating the Motive

To stress-test the conclusion rather than simply accept it, income records were pulled for all three physical-description matches. Miranda Priestly's annual income was roughly 30x Jeremy Bowers' consistent with his description of a wealthy employer. Notably, this check also proved that wealth alone wasn't a reliable filter: one of the two ruled-out women was nearly as wealthy as Miranda. It was the behavioral data the concert attendance pattern that actually closed the case, not the money. The financial data confirms motive, not identity.

One gap was also flagged rather than hidden: no interview record exists for Miranda Priestly herself. Her identification rests entirely on independently converging evidence — physical description, vehicle, social check-in behavior, and financial profile — not a confession.
