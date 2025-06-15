# Simple Task Board

## Motivation

I like having a task list that I can focus on. I get satisfaction from dragging tasks from to-do, to in-progress, to complete. If something distracts me, I have an easy mechanism to refocus on my work, by checking my task list.

Creating tasks is slow, and requires repetitive mouse and keyboard inputs. From my task board I click create task, which loads a new page, click on the text field for title, type in the title, click on the text field for description, type in the description, assign it to myself, click the labels dropdown, select the appropriate labels for this task, save, assign it to my personal task folder, click create. Wait for it to load. Navigate back to my task board. Wait for my tasks to load.

I want a board of small tasks that can be thrown away at the end of the day. I want to be able to whip up a new task in the time it takes me to type out its title.

## Design Focus

Accessible via web browser on desktop (not mobile), no internet required. Single page .html file with all javascript embedded in the page.

The page presents a simple task board, with 'To do', 'In progress', and 'Complete' columns.

It should not require a full displays worth of space. I want it to be effective even with a horizontal sliver of the tab open.

It should be extremely fast to create tasks with a keyboard alone, with hotkeys mapped to different actions.

The movement of tasks to different columns is manually done with drag and drop to highlight the meaning of it. Not by hotkey.

## User Interface

label colors (9: roygbiv, gray, brown)
  a row of colored squares
board columns:
  to do
  in progress
  complete
prep area (left of board, top left of page, that is not shown when nothing is there)

tasks are rectangles of the same size with rounded corners, showing the title of the task and a truncated description (when selected, the task grows vertically to fit the description)
the left 10% of the task rectangle is a colored strip showing the label colors

## Actions

These are actions that can be taken by the user. The action executed depends on the current input mode of the board.

DEFAULT:
T: Create task in the prep area. Enter EDIT_TASK mode.
Click on task: Select task. Enter TASK_SELECTED.
Double click: Select and edit task. Enter EDIT_TASK.

TASK_SELECTED:
(expands task in place to show description)
T: Move task to the prep area. Enter EDIT_TASK mode.
ESCAPE: Unselect task. Enter DEFAULT mode.
Click elsewhere: Unselect task. Enter DEFAULT mode.

EDIT_TASK:
T: Focus the title text box of the task. Enter EDIT_TASK_TEXT mode.
D: Focus the description text box of the task. Enter EDIT_TASK_TEXT mode.
0 through 9: Add this label to the task. If label is already assigned to the task, remove it.
Enter: Save the task and move it to its state. New tasks by default are assigned 'To do'. Existing tasks may be from 'In progress' or 'Complete'.

EDIT_TASK_TEXT:
Enter: Save the title and description text. Enter EDIT_TASK mode.
