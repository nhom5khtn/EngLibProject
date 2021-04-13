# EngLibProject
## 1 core:  3/5/2021
### class:
1. **pool** (2mem) : att: PriorQueue<Vocab> = vocab; num_vocab, (enum) CompleteState{DONE, FAILED}
+ user_pool: store user state 
=> case: add(new_vocab) -> isExist(new_vocab): check ?, why?
+ ref_pool: refference (load file json) 
+ *wordList*: json {num_vocab, vocab:[primary key, mean, question:[quest_types], essential,etc: sub key (synonym)]} - (1mem: Thuan)-(18/04/2021)
2. **vocab** (1mem) => Thuan
+ att = wotdList
+ method: parseString
3. **Account** (1mem: Phuoc)-(02/05/2021)
+ Account.kt
+ AccountViewModel.kt
+ AccountViewModelFactory.kt
+ AccountSingleton.kt
## 2 workflow: 10/5/2021
=> nullable_case
### class: 
1. **Store**:  LOADprocess, STOREprocess
2. **Configuration**: => export file config (1mem: Khang)-(09/05/2021)
+ Configuration.kt
+ ConfigurationViewModel.kt
+ ConfigurationViewModelFactory.kt
+ ConfigurationSingleton.kt
### Activity (KOTLIN file, LAYOUT file):
1. **Introduce**: (1mem: Quyen)-(09/05/2021
+ SplashActivity (contains Logo: name)
+ OnboardingActivity
+ WelcomeActivity
2. **Login**: (2mem: Phuoc, Hao)
+ **LoginActivity** (contains username, password) - (1mem: Phuoc)-(09/05/2021)
- transfer to: QuestionActivity
+ **SignupActivity** (contains fullname, username, password) - (1mem: Phuoc)-(09/05/2021)
- transfer to: LoginActivity
+ **QuestionActivity** - (1mem: Hao)-(09/05/2021)
- (num_quest follow file config) contains FAILED_button
- null_case: user_list = null => INIT_Notification
++ **ABCDActivity** (ABCD)
++ **FillActivity** (fill)
++ **BoolActivity** (T/F)
- loop follow numQuest in config file
+ **NotificationDialog**: - (1mem: Phuoc)-(09/05/2021)
- PASSED : transfer to: HomeActivity
- FAILED:
	wrong reply
	click btnGiveup  => Update CompleteState => devolope (score)
- INIT: ask to add: 
{
	Yes => transfer to: RegisterActivity.
	No  => transfer to: HomeActivity.
	}
3. **HomeActivity**: (3mem)
+ **btnRegister** 	-> transfer to: **RegisterActivity** (1mem: Thuan)-(09/05/2021)
- add new word into user_pool => input: 	pri_key
- newWord.verify() | userPool.verify(priKey: String) : check new word whether exists in WordList or not 
{ 	NOK - Dialog => loop;
	OK 	- newWord.addUserPool(userPool: UserPool) | userPool.addNew(priKey: String)
	}
- Display => output: 	vocab
+ **btnPrint** 		-> transfer to: **PrintActivity** (1mem: Hao)-(09/05/2021)
- listUser: print(user_pool)
- ListDict: print(ref_pool)
+ **btnSetup** 		-> transfer to: **SetupAcitvity** (1mem: Khang)-(09/05/2021)
- waitTime for displaying question (waitTimeQuest)
- number of questions (numQuest)
- ..
- => use Config class => modify file config
+ **btnDevelop**	:  New_Feature (score)

## 3 git, github (2mem: Phuoc, Khang) 5/4/2021
+ => entire process

## 4 report (1mem: Hao) 1/6/2021
 => document 		(word)
 => presentation 	(powerpoint)

## 5 unitest (1mem: Thuan) 12/4/2021

## Description's Project
store_pool
fisrt: init user_pool
using time: 
(Act)Login: 
=> add new word = galaxy (pri)
compare ref_pool => true: store user_pool 
---STOREprocess---
=> cur_state => save local (exports file user_wordList) => pre_state = cur_state (contains file user_wordList)

===========================================================
second: init user_pool = new  (pre_state)

user_list contains only pri_key
---LOADprocess---
loop(num_vocab)
	vocab = query(pri_key)
	user_pool.add(vocab)

using time: login: display question(pri) [follow essential]
quest (mean?)
display: pri_key
=> ABCD: mean
=> fill: non
=> t/f: 
quest (pri?)
display: mean
=> ABCD: pri
=> fill: 
=> t/f: {num_vocab: 20, 
	 vocab:[pri_key: mean,
		mean: to express or represent something such as an idea, thought, or fact, 
		question: [mean?: [ABCD: yes, fill: no, t/f: yes]; pri_key?: [ABCD: yes, fill: no, t/f: yes]],
		essential: high,
		etc: sub key (synonym)],
		
	}

