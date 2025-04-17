# cpushceduling
[11:45 pm, 28/3/2025] ̶✨: import heapq
import matplotlib.pyplot as plt

class Task:
    def _init_(self, name, execution_time, priority):
        self.name = name
        self.execution_time = execution_time
        self.priority = priority
        self.energy_consumption = 0

    def _lt_(self, other):
        return self.priority > other.priority  # Higher priority first

class EnergyEfficientScheduler:
    def _init_(self):
        self.task_queue = []
        self.cpu_frequency = 2.5  # Default frequency in GHz
        self.voltage = 1.2  # Default voltage in Volts
        self.base_power = 50  # Base power in Watts
        self.task_log = []  # Store task execution details

    def add_task(self, task):
        heapq.heappush(self.task_queue, task)
[11:45 pm, 28/3/2025] ̶✨: def adjust_cpu_frequency_and_voltage(self, task):
        if task.priority > 7:
            self.cpu_frequency = 3.5  # High priority -> Increase frequency
            self.voltage = 1.3
        elif task.priority > 4:
            self.cpu_frequency = 2.5  # Medium priority -> Moderate frequency
            self.voltage = 1.2
        else:
            self.cpu_frequency = 1.5  # Low priority -> Lower frequency to save energy
            self.voltage = 1.1
        print(f"CPU Frequency adjusted to: {self.cpu_frequency} GHz, Voltage adjusted to: {self.voltage} V")
[11:45 pm, 28/3/2025] ̶✨: def calculate_energy(self, task):
        return self.base_power * (task.execution_time / self.cpu_frequency) * (self.voltage ** 2)

    def execute_tasks(self):
        print("Executing Tasks with Energy-Efficient Scheduling using DVFS...")
        while self.task_queue:
            task = heapq.heappop(self.task_queue)
            self.adjust_cpu_frequency_and_voltage(task)
            task.energy_consumption = self.calculate_energy(task)
            self.task_log.append((task.name, self.cpu_frequency, self.voltage, task.energy_consumption))
            print(f"Executing {task.name} | Priority: {task.priority} | Execution Time: "
                  f"{task.execution_time} ms | Energy Used: {task.energy_consumption:.2f} J")
        self.plot_results()
