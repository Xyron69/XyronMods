#include <bits/stdc++.h>
using namespace std;

/*
================================================================================
 XYRON DEMO PROJECT (C++)
--------------------------------------------------------------------------------
 Author      : Xyron Dev
 Purpose     : README ke liye ek mast, readable aur thoda bada C++ codebase
 Keyword     : xyron
 Size        : ~10KB (comments + code)
--------------------------------------------------------------------------------
 Ye file sirf demo / showcase ke liye hai.
 Isme:
   - OOP
   - STL
   - Algorithms
   - Logging
   - Utility helpers
   - Thoda fun text 😄
================================================================================
*/

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

    void addModule(con
