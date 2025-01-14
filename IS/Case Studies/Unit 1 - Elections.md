### Applying the Basic Concepts

- Now that we have learned some of the basic concepts and vocabulary of InfoSec, we're going to apply it to something (fairly) topical, elections.
- We're going to analyse how UK general elections are organised to figure out the vulnerabilities that they have, the threats to which they are subject and the controls that have been implemented to minimise the threats.

### So how are UK elections organised?

- General elections take place once every 5 years, or less if the government in power decides to "go to the polls" sooner (subject to some constraints that we don't care about here).
- The UK is divided into several hundred constituencies.
- Each constituency is represented in parliament by a single __Member of Parliament__, who is typically a member of a political party.
- A citizen who lives in a constituency who votes for whichever of the __candidates__ standing to be the constituency's MP they wish to represent them.
- The candidate who gets the most votes, becomes the MP.
- To have a vote (i.e. to be a voter) a citizen must fulfil a number of criteria mostly concerned with citizenship and age and they must be registered to vote.
- When registered to vote, they will be told which of the __polling stations__ around the constituency (usually the polling station nearest to their home) they must go to in order to cast their vote.
- On election day, a voter goes to the polling station and has their name checked against the electoral roll for that polling station.
- Once their name is checked off, the voted is handed a __ballot paper__ listing the names of all the candidates standing for election in that constituency.
- The voter, in a private booth, puts a cross against the candidate they vote for.
- They then place their ballot in the ballot box.
- At the close of the polls, the ballot box is sealed and transported to the constituency's __counting station__ where, along with every other of the constituency's ballot boxes, it is emptied and the votes counted by a team of officials.
- When the count is complete, the candidate with the most votes is declared the Member of Parliament for the constituency.

### Why is Security Important?

- Elections in the UK don't use much technology, in contrast to many other countries.
- Nevertheless, security is important in general elections to ensure that the vote is fair and reflects the will of the voters.

### Voting Assets

- What are the assets that need to be secured?
	- The electoral toll
	- Voting slips
	- Ballot boxes
	- The result

### Which security goals are important?

- __Confidentiality__
	- A vote must be confidential to the voter - no-one should be able to find out for which candidate the voter cast their vote.
	- __Why?__
		- To avoid discrimination or persecution by the Government of citizens that didn't vote for them.
		- To prevent vote buying.
		- To prevent voter coercion.
- __Integrity__
	- Once a vote has been cast for a particular candidate, that vote cannot be changed.
	- __Why?__
		- To avoid ensure fairness and ensure confidence
	- A voter can only vote once
	- __Why?__
		- To avoid ballot stuffing
- __Availability__
	- Voters must have access to polling stations.
	- __Why?__
		- So they are able to cast their votes.
	- Polling station officials must have access to the electoral roll.
	- __Why?__
		- So they can validate voters.

### Vulnerabilities

- What are the election system's vulnerabilities?
	- No voter ID is required at the polling station.
	- The voting slip carries a unique serial number.
	- Votes are counted by humans and humans are fallible.

### (Some) Threats

- Ballot Stuffing.
- Voter Coercion.
- Vote Buying.
- Returning a false count.

### Controls

- __Ballot Stuffing__
- Attack:
	- __1. Impersonating voters. Exploits no voter ID vulnerability__
		- Control: Implausible that enough people could be recruited to impersonate voters to have a significant effect; fraud would be easily detected.
	- __2. Casting multiple votes__
		- Control: Designated polling station and voter's name crossed off when handed ballot paper.
	- __3. Intercepting ballot box on way to counting station and replacing ballot papers with false ones__
		- Control: Ballot boxes sealed; Strict protocol for secure transfer of ballot boxes.
- __Voter Coercion__
- Attack:
	- __1. Voter is forced to vote for a particular candidate.__
		- Control: Private voting booths; Voting slips must be placed directly in ballot boxes and no photography allowed inside polling station, hence impossible for voter to prove how they voted in person applying coercion.
	- __2. Voter fears retribution by government if they vote against it. Exploits polling card serial number.__
		- Control: Effort required to identify voters too large.
- __Vote Buying__
- Attack:
	- __1. Voter is offered incentive to vote for a particular candidate.__
		- Control: As voter coercion.
- __Returning a false count__
- Attack:
	- __1. Counting station staff coerced or offered incentives to manipulate vote count; Exploits human vote counter fallibility.
		- Control: Large numbers of people would have to be coerced/bribed to guarantee desired outcome; Counts are checked; Recounts are requested; Independent observers present at count

### Which security goals achieved?

- Confidentiality: yes
- Integrity: yes
- Availability: hmm...

- _Can you identify how threats to availability are controlled?_

### Electronic Voting

- Many countries use electronic voting (in various ways), and it has been suggested that the UK should adopt electronic voting.
- __Why?__
	- Faster results.
	- (Potentially) more accurate.
	- Ease of voting should lead to an increase in participation in elections.
- But what are the risks?
- Are the vulnerabilities, threats and controls the same?