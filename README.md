# currencyconverter
#include <iostream>
#include <map>
#include <fstream>
#include <string>
#include <iomanip>

// Function to load conversion rates from an external file
void loadConversionRates(std::map<std::string, double>& rates, const std::string& filename) {
    std::ifstream file(filename);
    if (!file.is_open()) { // Check if the file is successfully opened
        std::cerr << "Unable to open file. Using default rates." << std::endl;
        return;
    }

    std::string currency;
    double rate;
    
    // Read data from the file line by line
    while (file >> currency >> rate) {
        rates[currency] = rate; // Add the currency and its rate to the map
    }
    
    file.close();
}

// Function to display available currencies
void displayCurrencies(const std::map<std::string, double>& rates) {
    std::cout << "Available currencies:\n";
    for (const auto& pair : rates) {
        std::cout << pair.first << " ";
    }
    std::cout << "\n";
}

// Function to convert currency
double convertCurrency(const std::map<std::string, double>& rates, const std::string& from, const std::string& to, double amount) {
    if (rates.find(from) == rates.end() || rates.find(to) == rates.end()) {
        std::cerr << "Currency not found.\n";
        return 0;
    }
    double fromRate = rates.at(from);
    double toRate = rates.at(to);
    return (amount / fromRate) * toRate;
}

int main() {
    std::map<std::string, double> conversionRates = {
        {"USD", 1.0},   // US Dollar
        {"EUR", 0.85},  // Euro
        {"GBP", 0.75},  // British Pound
        {"INR", 74.0},  // Indian Rupee
        {"JPY", 110.0}, // Japanese Yen
        {"CAD", 1.25},  // Canadian Dollar
        {"AUD", 1.35}   // Australian Dollar
    };

    loadConversionRates(conversionRates, "rates.txt");  // Load rates from a file if available

    std::string fromCurrency, toCurrency;
    double amount;

    while (true) {
        displayCurrencies(conversionRates);
        std::cout << "Enter source currency (or 'exit' to quit): ";
        std::cin >> fromCurrency;
        if (fromCurrency == "exit") break;
        
        std::cout << "Enter target currency: ";
        std::cin >> toCurrency;
        
        std::cout << "Enter amount to convert: ";
        std::cin >> amount;

        double result = convertCurrency(conversionRates, fromCurrency, toCurrency, amount);
        std::cout << std::fixed << std::setprecision(2);
        std::cout << amount << " " << fromCurrency << " = " << result << " " << toCurrency << "\n\n";
    }

    return 0;
}
