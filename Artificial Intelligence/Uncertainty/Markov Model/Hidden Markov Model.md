## Definition

- A type of a Markov model for a system with hidden states that generate some observed event
- Sometimes the AI has some measurement of the world but no access to the precise state of the world
	- Hidden state: the state of the world
	- Observations: whatever data the AI has access to

## Examples

### Robot

- A robot exploring uncharted territory
- Hidden state: its position
- Observation: the data recorded by the robot’s sensors

### Speech recognition

- Hidden state: the words that were spoken
- Observation: the audio waveforms

### User engagement

- Measuring user engagement on websites
- Hidden state: how engaged the user is
- Observation: the website or app analytics

### Weather prediction

- Hidden state: the weather
- Observation: indoor camera that records how many people brought umbrellas with them
- **Sensor model** (aka **emission model**, also see [[Sensor Markov Assumption]]):

||$E_{umbrella}$|$E_{no umbrella}$|
|:-:|:-:|:-:|
|$X_{sun}$|0.2|0.8|
|$X_{rain}$|0.9|0.1|