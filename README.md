# freecodecamp
Mean-Variance-Standard Deviation Calculator
# test_module.py
import unittest
import numpy as np
from mean_var_std import process_data

class TestProcessData(unittest.TestCase):
    def test_process_data(self):
        # Create a temporary 'data.txt' file to test
        data = '''29,97,32,100,45
15,88,5,75,22
'''
        with open('data.txt', 'w') as f:
            f.write(data)

        # Expected result after flattening and selecting specific indices
        expected_result = np.array([29., 32., 45., 15.,  5., 22.])

        # Call the function and check if the result is as expected
        result = process_data('data.txt')
        np.testing.assert_array_equal(result, expected_result)
        
    def test_invalid_file(self):
        # Test the case when the file doesn't exist
        with self.assertRaises(OSError):
            process_data('non_existing_file.txt')

def run_tests():
    unittest.main(argv=[''], exit=False)

