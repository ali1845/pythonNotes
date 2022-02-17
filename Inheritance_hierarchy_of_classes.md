
# Hierarchy of classes

  - To create class hierarchies, Inheritance is used.
  - The related classes will share a common **Interface** class.
  - Derived classes can specialize the interface by providing a particular implementation where it applies.

**Example**
  - Model an HR system.
  - HR system will process the payroll for the company's employees.
  - There are differnt types of employees in the company.
  - Our **Interface** class will be the **PayrollSystem**
  - **Base class** will be **Employee**.
  - And there are differnt types of employees, which will be *drived* from the *Employee* class.
  - **Drived classes** will be; **SalaryEmploee, HourlyEmployee and CommissionEmployee.**

  1. Lets start with creating the **PayrollSystem** class

          # Interface Class
          class PayrollSystem:
              # calculate payroll function takes a list of employees as an argument
              def calculate_payroll(self, employees):
                  print('Following are the payroll of the employee(s)')
                  print('---------------------------------------------')
                  for emp in employees:
                      print(f'Payroll for: {emp.id} -> {emp.name}')
                      print(f'Amount: {emp.calculate_payroll()}')
                      print('')

  2. Now create the Base class, **Employee**.

          # Base class

          class Employee:
              def __init__(self, id, name):
                  self.id = id
                  self.name = name

  3. Some employees have fixed salaries so drive a class of **SalaryEmploee** from **Employee.**

          ## HR system requires that every type of Employee must implement .calculate_payroll() method
          ## that returns the weekly salary of the employee.

          # Derived class SalaryEmployee from Employee

          class SalaryEmployee(Employee):
              def __init__(self, id, name, weekly_salary):
                  super().__init__(id, name)
                  self.weekly_salary = weekly_salary

              def calculate_payroll(self):
                  return self.weekly_salary


  4. Some of the employees get paid hourly. A class of **HourlyEmployee** will be drived.

          # Derived class for hourly working employee from Employee
          class HourlyEmployee(Employee):
              def __init__(self, id, name, hours_worked, hour_rate):
                  super().__init__(id, name)
                  self.hours_worked = hours_worked
                  self.hour_rate = hour_rate

              def calculate_payroll(self):
                  return self.hours_worked * self.hour_rate

  5. A class of **CommissionEmployee** for those Employees that also get commissions along with their salaries, can extend the functionalities of **SalaryEmploee** class.

    - That means *CommissionEmployee* will be derived from *SalaryEmploee*

            # Derived class for commission based employee from the class SalaryEmployee

            class CommissionEmployee(SalaryEmployee):
                def __init__(self, id, name, weekly_salary, commission):
                    super().__init__(id, name, weekly_salary)
                    self.commission = commission

                def calculate_payroll(self):
                    fixedSal = super().calculate_payroll()
                    return fixedSal + self.commission


  6. Now create a program file to output the results.

          # HR_program.py

          import HR_System_OOPs as hr

          Sal_emp = hr.SalaryEmployee(1, 'Ali', 10000)
          hr_emp = hr.HourlyEmployee(2, 'Rubiya', 28, 500)
          cm_emp = hr.CommissionEmployee(3, 'Bilal', 9000, 5000)
          payroll_sys = hr.PayrollSystem()

          payroll_sys.calculate_payroll([
              Sal_emp,
              hr_emp,
              cm_emp
              ])

            # Results

            Following are the payroll of the employee(s)
            ---------------------------------------------
            Payroll for: 1 -> Ali
            Amount: 10000

            Payroll for: 2 -> Rubiya
            Amount: 14000

            Payroll for: 3 -> Bilal
            Amount: 14000
