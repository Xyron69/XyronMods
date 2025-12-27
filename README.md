#include <bits/stdc++.h>
using namespace std;

/*
================================================================================
 XYRON DEMO PROJECT (C++)
--------------------------------------------------------------------------------
 Author      : Xyron Dev
 Purpose     : README
 Keyword     : xyron
 Size        : ~10KB 
--------------------------------------------------------------------------------
   - OOP
   - STL
   - Algorithms
   - Logging
   - Utility helpers
================================================================================

// ----------------------------- LOGGER -----------------------------------------
class Logger {
public:
    enum Level { INFO, WARNING, ERROR };

    static void log(const string& msg, Level lvl = INFO) {
        cout << timeStamp() << " [" << levelToString(lvl) << "] " << msg << '\n';
    }

private:
    static string levelToString(Level lvl) {
        switch (lvl) {
            case INFO: return "INFO";
            case WARNING: return "WARNING";
            case ERROR: return "ERROR";
        }
        return "UNKNOWN";
    }

    static string timeStamp() {
        time_t now = time(nullptr);
        tm* ltm = localtime(&now);
        char buf[32];
        sprintf(buf, "%02d:%02d:%02d", ltm->tm_hour, ltm->tm_min, ltm->tm_sec);
        return string(buf);
    }
};

// ----------------------------- UTILS -------------------------------------------
namespace Utils {
    string toUpper(string s) {
        transform(s.begin(), s.end(), s.begin(), ::toupper);
        return s;
    }

    bool isPrime(int n) {
        if (n < 2) return false;
        for (int i = 2; i * i <= n; ++i)
            if (n % i == 0) return false;
        return true;
    }

    vector<int> generatePrimes(int limit) {
        vector<int> primes;
        for (int i = 2; i <= limit; ++i)
            if (isPrime(i)) primes.push_back(i);
        return primes;
    }
}

// ----------------------------- CORE CLASS --------------------------------------
class XyronEngine {
private:
    string engineName;
    int version;
    vector<string> modules;

public:
    XyronEngine(string name = "xyron", int ver = 1)
        : engineName(name), version(ver) {
        Logger::log("XyronEngine initialized");
    }

    void addModule(const string& module) {
        modules.push_back(module);
        Logger::log("Module added: " + module);
    }

    void listModules() const {
        Logger::log("Listing all modules:");
        for (const auto& m : modules)
            cout << "  - " << m << '\n';
    }

    void runDiagnostics() const {
        Logger::log("Running diagnostics for engine: " + engineName);
        Logger::log("Version: " + to_string(version));
        Logger::log("Total modules: " + to_string(modules.size()));
    }
};

// ----------------------------- DATA MODEL --------------------------------------
struct User {
    int id;
    string name;
    string role;

    string toString() const {
        return "User{id=" + to_string(id) + ", name=" + name + ", role=" + role + "}";
    }
};

// ----------------------------- ALGORITHMS --------------------------------------
namespace Algorithms {
    int fibonacci(int n) {
        if (n <= 1) return n;
        int a = 0, b = 1;
        for (int i = 2; i <= n; ++i) {
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }

    void sortUsersByName(vector<User>& users) {
        sort(users.begin(), users.end(), [](const User& a, const User& b) {
            return a.name < b.name;
        });
    }
}

// ----------------------------- DEMO FUNCTIONS ----------------------------------
void demoUsers() {
    vector<User> users = {
        {1, "Aman", "Admin"},
        {2, "Ravi", "Editor"},
        {3, "Neha", "Viewer"}
    };

    Algorithms::sortUsersByName(users);
    Logger::log("Sorted users:");
    for (const auto& u : users)
        cout << u.toString() << '\n';
}

void demoMath() {
    Logger::log("Fibonacci demo:");
    for (int i = 0; i < 10; ++i)
        cout << "fib(" << i << ") = " << Algorithms::fibonacci(i) << '\n';

    auto primes = Utils::generatePrimes(50);
    Logger::log("Prime numbers up to 50:");
    for (int p : primes) cout << p << " ";
    cout << '\n';
}

// ----------------------------- ASCII FUN ---------------------------------------
void printBanner() {
    cout << R"(
 __   __  __   __  _______  _______  __    _
|  |_|  ||  |_|  ||       ||       ||  |  | |
|       ||       ||   _   ||   _   ||   |_| |
|       ||       ||  | |  ||  | |  ||       |
|       || ||_|| ||  |_|  ||  |_|  ||  _    |
| ||_|| || |   | ||       ||       || | |   |
|_|   |_||_|   |_||_______||_______||_|  |__|

            powered by xyron
    )" << '\n';
}

// ----------------------------- MAIN --------------------------------------------
int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    printBanner();

    XyronEngine engine("xyron-core", 2);
    engine.addModule("auth");
    engine.addModule("database");
    engine.addModule("network");
    engine.listModules();
    engine.runDiagnostics();

    demoUsers();
    demoMath();

    Logger::log("Xyron demo program finished successfully.");
    return 0;
}

/*
================================================================================
 NOTES:
--------------------------------------------------------------------------------
 - This code is internaly for fun (README showcase for)
 - Real production 
 - You can  this file  freely modify 
================================================================================

