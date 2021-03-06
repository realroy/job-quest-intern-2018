### TakeMeTour Internship Program 2018

Hi all applicants! Welcome to TakeMeTour Internship Program 2018. Being and intern at TakeMeTour is challenging so we have challenges for you! These challenges are designed to assess your learning skill, which is the fundamental and most important skill of great software developer. So I do not expect you to have full or any knowledge about the topic beforehand but it's your job to try to learn and answer those challenges.

## Algorithm in Javascript
Code must be writted in Javascript language. The code will be tested with Node8, so you can use all Javascript features that equivalent to Node8.

1. Write a function that shift the elements of array to left or right by n elements in infinity loop. the function recevice 3 parameters, 1st is an array, 2nd the is direction ('left' or 'right'), 3rd is the number of elements will be shifted. For example,
```
> shift(['john', 'jane', 'sarah', 'alex'], 'left', 2)
['sarah', 'alex', 'john', 'jane']

> shift([1, 2, 3, 4 ,5], 'right', 3)
[3, 4, 5, 1, 2]
```
Answer:
```javascript
function initStartPoint (arrayLength, direction, num) {
	if (num < 0 && num >= arrayLength)
  	throw new Error('Second parameter should >= 0 and < first parameter length!')
  switch(direction) {
  	case 'left':	return num
   	case 'right':	return arrayLength - num
  	default:	throw new Error('Third parameter should be "left" or "right"!')
  }
}

function shift (array, direction, num) {
	if(!Array.isArray(array))
  	throw new Error('First parameter should be an "Array"!')
	const arrayLength = array.length
	let index = initStartPoint(arrayLength, direction, num)
	const result = []
	while(true) {
		if(result.length === arrayLength)
			return result
	index = index === arrayLength ? 0 : index
  	result.push(array[index++])
	}
}
```
2. Download [hero.json](https://github.com/takemetour/job-quest-intern-2018/blob/master/hero.json) and write a code to caculate these values from **hero.json**
- 2.1 Average **networth** of all heroes
- 2.2 Average **level** for hero that has 'intelligent' as **primary_attribute**
- 2.3 Find the hero who got the most **assist**
- 2.4 Find the hero who got the worst **kill/death ratio** (ratio = kill/death)

Answer:
```javascript
const hero = {
  json: require('./hero.json')
}
// helper function that calculate average of entirely array with one specific attribute(key) of object in that array.
function getAverageWhereAttribute(array = [], attribute = '') {
	const initialAccumulate = 0
	const sum = array.reduce((accumulate, each) => accumulate + each[attribute], initialAccumulate)
	const n = array.length
	return sum/n
}

const FIRST_ELEMENT = 0

// 2,1
const averageNetworth = getAverageWhereAttribute(hero.json, 'networth')

// 2.2
const intHero = hero.json.filter(hero => hero.primary_attribute === 'intelligent')
const averageLevelOfIntHero = getAverageWhereAttribute(intHero, 'level')

// 2.3
const theMostAssistHero = hero.json.sort((a, b) => a.assist < b.assist)[FIRST_ELEMENT]

// 2.4
const wostKillDeadRatio = hero.json.sort((a, b) => (a.kill / a.death) > (b.kill / b.death) )[FIRST_ELEMENT]
```

## Simple Web Application: A joke from Chuck Norris.

This part of quest will be a challenging one. You are going to make a simple web application which allow users to get some joke from **Chuck Norris** himself.

> Chuck Norris once ordered a Big Mac at Burger King, and got one.

[Github repo](https://github.com/realroy/joke-from-chuck-norris)

### Features
- Users can get a joke from [Chuck Norris API](http://www.icndb.com/api/)
- Users has options to change number of result jokes, user's first name and last name
- UI Design as you wish.

### Technical description
- Using data from [REST API](http://www.icndb.com/api/)
- Any tools & framework is allowed.
- If you are using tools & framework which is same as our tech stack (React, Redux, styled-components, recompose etc.) will be a plus.
- Any extra feature will be a plus.

## Questions
Q1: What is GraphQL and how it is different from REST API?

A1:
```
 New way to query data which provide flexibility to retreive data between Client-Server more than REST API with no added logic for new structure of data. 
```


Q2: Please explain how javascript benefits from cross-platform development

A2:
```
* Developer team don't have to learn serveral languages.
* Easy to share code and logic across vary platfrom.
* Easy to maintain code.
```

Q3: What do you expect to get from during an internship at TakeMeTour?

A3:
```
Dive deep in javascript technology.
```

## Submitting

Please fork this repo and submit your repository at jet@takemetour.com along with your contact information.

Note: These challenges must be done by yourself. There is no benefit for both sides if the answer do not reflect your true skill.
