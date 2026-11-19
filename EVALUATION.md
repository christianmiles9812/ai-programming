
# Agent Lab Part 4 – Code Evaluation

## 1. Testing Prompt

I used ChatGPT to generate five Python tests based on the assignment requirements. The tests were designed to check library lookup, tutoring aliases, case-insensitive searches, invalid resources, and listing all available resources.

## 2. Final Test Code

I created `test_agent.py` inside the `campus_agent` folder.

The file contains five tests:

- `test_library_lookup` - Checks that searching for library returns the correct information.
- `test_tutoring_alias` - Checks that the tutoring alias returns the Tutoring Center.
- `test_case_insensitive` - Checks that uppercase searches still work.
- `test_resource_not_found` - Checks that an invalid resource returns an error.
- `test_list_all_resources` - Checks that searching for all returns at least four resources.

## 3. Test Results

All five tests passed when I ran them locally using pytest. I also pushed the tests to GitHub and verified that they passed through GitHub Actions.

During testing, I ran into an issue because the original tests were looking for a "resource" key that did not exist in the returned dictionary. I checked the actual output from my function and corrected the tests to match its structure.

## 4. Changes to the Test Code

I changed the three name checks to use `result["name"]` instead of `result["resource"]["name"]`. This matched how my existing agent function returned its information.

I did not need to change the original agent function because it was already working correctly.

## 5. CI/CD Workflow Prompt

I used ChatGPT to help create a GitHub Actions workflow based on the assignment requirements. It needed to run whenever code was pushed to the main branch, install Python 3.11 and the required dependencies, and execute the pytest tests.

## 6. Final Workflow

I created `.github/workflows/test.yml` in the root of my repository.

The workflow:
- Triggers whenever code is pushed to the main branch.
- Checks out the repository.
- Sets up Python 3.11.
- Installs pytest and the project dependencies.
- Runs the five tests inside the `campus_agent` folder.

The workflow successfully ran through GitHub Actions, and all steps completed successfully.

## 7. Changes to the Workflow

I included the installation of the project's `requirements.txt` file because the agent uses Google ADK and needs those dependencies to run.

I also made sure the workflow used the correct working directory when running the tests.

## 8. Reflection

### Was the AI-generated code better or worse than what you would write? How?

I think the AI-generated code was helpful because it saved time and gave me a starting point. However, it wasn't completely correct the first time. I still had to check how my existing function worked and make changes so the tests matched the actual output.

### Did you find any code erosion or verbosity in the AI's output?

I didn't notice much code erosion in this assignment because the test file was fairly small. However, I did run into an issue where the generated tests expected a different dictionary structure than what my program actually returned. This showed me why it's important to review AI-generated code instead of just copying it.

### What would you do differently next time you prompt an AI for code?

Next time, I would provide more information about my existing code and how my functions are structured. I would also ask the AI to check its output against my existing project before suggesting changes.

### What impact would this app have on students at JCC?

I think the Campus Resource Assistant could make it easier for students to find information about campus resources without having to search through different websites or contact multiple departments. It could help students quickly find things like library information, tutoring, and other campus services.

Overall, I think it would be a useful starting point for making campus information easier to access.
