# Site-Monitoring-Dashboard
class SiteEngineerDashboard
{
    static List<string> attendanceList = new List<string>();
    static string savedChecklist = "";
    static void Main()
    {
        while (true)
        {
            Console.Clear();
            Console.WriteLine("=== Site Engineer Dashboard ===");
            Console.WriteLine("1. Daily Progress Tracker");
            Console.WriteLine("2. Material Strength Monitor");
            Console.WriteLine("3. Safety Checklist");
            Console.WriteLine("4. Worker Attendance");
            Console.WriteLine("5. Site Summary");
            Console.WriteLine("6. Exit");
            Console.Write("Select an option (1-6): ");

            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    DailyProgressTracker();
                    break;
                case "2":
                    MaterialStrengthMonitor();
                    break;
                case "3":
                    SafetyChecklist();
                    break;
                case "4":
                    WorkerAttendance();
                    break;
                case "5":
                    SiteSummary();
                    break;
                case "6":
                    Console.WriteLine("Exiting... Stay safe on site!");
                    return;
                default:
                    Console.WriteLine("Invalid choice. Press Enter to try again.");
                    Console.ReadLine();
                    break;
            }
        }
    }

    static void DailyProgressTracker()
    {
        Console.Clear();
        Console.WriteLine("=== Daily Progress Tracker ===");

        for (int i = 1; i <= 5; i++)
        {
            Console.Write($"Enter task {i}: ");
            string task = Console.ReadLine();
            Console.WriteLine($"✅ Task {i} recorded: {task}");
        }

        Console.WriteLine("Press Enter to return to menu.");
        Console.ReadLine();
    }

    static void MaterialStrengthMonitor()
    {
        Console.Clear();
        Console.WriteLine("=== Material Strength Monitor ===");

        string material;
        while (true)
        {
            Console.Write("Enter material name (or type 'done' to finish): ");
            material = Console.ReadLine();

            if (material.ToLower() == "done") break;

            Console.Write($"Enter strength value for {material}: ");
            string strength = Console.ReadLine();

            Console.WriteLine($"📊 {material} strength recorded: {strength}\n");
        }

        Console.WriteLine("Press Enter to return to menu.");
        Console.ReadLine();
    }

    static void SafetyChecklist()
    {
        Console.Clear();
        Console.WriteLine("=== Safety Checklist ===");

        string checklist;
        do
        {
            Console.Write("Enter today's safety checklist (e.g., PPE check, scaffolding inspection): ");
            checklist = Console.ReadLine();

            if (string.IsNullOrWhiteSpace(checklist))
            {
                Console.WriteLine("Checklist cannot be empty. Please try again.\n");
            }

        } while (string.IsNullOrWhiteSpace(checklist));

        savedChecklist = checklist;
        Console.WriteLine($"\n✅ Checklist saved: {checklist}");
        Console.WriteLine("Press Enter to return to menu.");
        Console.ReadLine();
    }

    static void WorkerAttendance()
    {
        Console.Clear();
        Console.WriteLine("=== Worker Attendance ===");

        attendanceList.Clear();
        Console.Write("How many workers to mark present today? ");
        if (int.TryParse(Console.ReadLine(), out int count))
        {
            for (int i = 1; i <= count; i++)
            {
                Console.Write($"Enter name of worker {i}: ");
                string name = Console.ReadLine();
                attendanceList.Add(name);
            }

            Console.WriteLine("\n✅ Attendance recorded.");
        }
        else
        {
            Console.WriteLine("Invalid number. Try again.");
        }

        Console.WriteLine("Press Enter to return to menu.");
        Console.ReadLine();
    }

    static void SiteSummary()
    {
        Console.Clear();
        Console.WriteLine("=== Site Summary ===");

        Console.WriteLine($"Safety Checklist: {(string.IsNullOrEmpty(savedChecklist) ? "Not recorded" : savedChecklist)}");
        Console.WriteLine("Workers Present:");
        if (attendanceList.Count == 0)
        {
            Console.WriteLine("None recorded.");
        }
        else
        {
            foreach (var worker in attendanceList)
            {
                Console.WriteLine($"- {worker}");
            }
        }

        Console.WriteLine("\n📌 Summary complete. Press Enter to return to menu.");
        Console.ReadLine();
    }
}
