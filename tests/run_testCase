import pytest
import sys
import os



def execute_workspace_tests():
    """
    Programmatically invokes pytest inside the Databricks cluster runtime,
    ensuring exit codes are mapped back to the OS layer for CI/CD tracking.
    """
    print("=" * 80)
    print("🚀 Starting Automated Pytest Suite Execution on Databricks Cluster...")
    print("=" * 80)



    # Define paths relative to the Workspace root
    project_root = "/Workspace/Users/jatin.march1993.arora@gmail.com/PEI_Project/Pyspark_Project"
    test_file = os.path.join(project_root, "tests", "test_analytics.py")

    # Force Python's compiler to recognize this local folder structure 
    sys.path.append(project_root)
    os.chdir(project_root)

    # Run pytest directly against the target file path string
    exit_code = pytest.main(["-v", test_file])

    if exit_code != 0:
        raise Exception("Unit testing suite failed!")


    # 1. Define the absolute path to your test file or test directory
    # target_test_path = "/Workspace/Users/jatin.march1993.arora@gmail.com/PEI_Project/Pyspark_Project/tests/test_analytics.py"

    # 2. Configure Pytest flags:
    # '-v' : Verbose output (lists each test case name clearly)
    # '-s' : Disables stdout capturing (allows print statements to show up live in logs)
    pytest_args = [
        "-v",
        "-s",
        test_file
    ]

    print(f"📋 Target Test Path Recognized: {test_file}\n")

    # 3. Invoke pytest programmatically
    # pytest.main returns an ExitCode enum (0 for success, 1 for failures, etc.)
    exit_code = pytest.main(pytest_args)

    print("\n" + "=" * 80)
    print(f"🏁 Test Suite Run Finished with Exit Code: {exit_code}")
    print("=" * 80)

    # 4. Bubble the exit code out to the system environment
    # Critical step: Without sys.exit(), Databricks will report a "SUCCESS" 
    # even if all your assertions failed!
    sys.exit(exit_code)

if __name__ == "__main__":
    execute_workspace_tests()