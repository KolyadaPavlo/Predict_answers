




* It is a mission to predict whether a student will get the right answer or not when he or she encounters a new question through learning data from students studying mathematics. Provide data for training and metadata surrounding it, and freely utilize the tools and methodologies you have to present a right or wrong prediction model.




### `curriculum-info.json`

*Metadata corresponding to Curriculum (grade) in mathematics curriculum with Curriculum-Chapter-Lesson-Unit. One Curriculum has multiple chapters.

* field information 
  * `id`: curriculum ID(Number)
  * `name`: name of curriculum(String)


### `chapter-info.json`

* Metadata corresponding to Chapter in a mathematics curriculum consisting of Curriculum-Chapter-Lesson-Unit. One Chapter has multiple Lessons.

* field information
  * `id`: chapter ID(Number)
  * `curriculum_id`: chapter inside curriculmn ID(Number)
  * `seq`: The order in which these chapters appear in your curriculum
  * `name`: chapter name(String)


### `lesson-info.json`

* Metadata corresponding to Lesson in a mathematics curriculum consisting of Curriculum-Chapter-Lesson-Unit. Lesson has multiple units, and one unit can belong to multiple Lessons.

* field information 
  * `id`: lesson ID(Number)
  * `chapter_id`: lesson inside chapter ID(Number)
  * `seq`: The order in which the lesson appears in your chapter.(Number)
  * `name`: lesson name(String)


### `unit-info.json`

* Metadata corresponding to Unit knowledge in mathematics curricula consisting of Curriculum-Chapter-Lesson-Unit.

* field information
  * `id`: unit of knowledge ID(Number)
  * `name`: unit of knowledge name(String)
  * `lessons`: List of lessons to which unit knowledge belongs(Array)
    * `id`: The lesson ID to which the unit knowledge belongs(Number)
    * `tier`: True if unit knowledge appears as a body problem in the lesson, false if only as a step problem


### `unit-dependency.json`

* Unit is the unit knowledge of a math problem. Some knowledge has prior knowledge to study that knowledge (for example, knowledge of factorization and quadratic equations is required to solve quadratic equations), which is data on this dependency graph.

* field information 
  * `id`: unit knowledge ID(Number)
  * `dependencies`: Arrangement of pre-knowledge IDs to study the unit knowledge(Array)


### `train.csv`

* This is the study data of students that will be used as a training set. It contains questions solved by students and data for right or wrong answers.

* Column Description
* 'id': Record Sequence (int)
* 'user_id': Student ID(int)
* 'unit_id': unit knowledge ID(int)
* 'result': Correct or wrong answer (0/1)
* 'modified_at': Record final modification timestamp (when correcting results after problem, this is the time stamp at the time of change)
* 'type': Record type
* 'LESSON': Records generated during lesson learning
* 'REVIEW': Records generated from lesson reviews after lesson learning
* 'CHAPTERREVIEW': Records generated from Chapter review after chapter learning
* 'PLACEMENTEST': Records generated from diagnostic evaluations
* 'is_step': whether it is a step problem (bool)
* `problem_id`: 문항 ID(int)
* Each unit knowledge is created into multiple questions using different values (for example, different coefficients in the "secondary factorization" unit knowledge).
* 'created_at': the first time stamp of a record (the time stamp when the problem log is generated prior to the problem)






## requirement

* Create a model that generates the 'submission.csv' file with the following two columns:
* 'id': Column value of test data (can be changed in order)
* 'result': Column value of test set record with corresponding 'id' predicted through model

You may also refer to the example result file 'submission-example.csv'.

* Please briefly specify how to run the model through the README file.

* Please briefly explain how you constructed your model through the README file, what assumptions you made, and why you made them.

* Some of the data in the training set may not meet the specifications specified above. The data preprocessing process is also intentionally placed so that it can be as close to the Real World dataset as possible, so you can process it in the appropriate way.

