# CppZoo-Final-Project

#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <ctime>
#include <cstdlib>

using namespace std;


const string HYENA = "hyena";
const string LION = "lion";
const string BEAR = "bear";
const string TIGER = "tiger";
const string HYENA_HABITAT = "Hyena Habitat";
const string LION_HABITAT = "Lion Habitat";
const string BEAR_HABITAT = "Bear Habitat";
const string TIGER_HABITAT = "Tiger Habitat";


const string HYENA_NAMES[11] = {"Shenzi", "Banzai", "Ed", "Zig", "Bud", "Lou", "Kamari", "Wema", "Nne", "Madoa", "Prince Nevarah"};
const string LION_NAMES[12] = {"Scar", "Mufasa", "Simba", "Kiara", "King", "Drooper", "Kimba", "Nala", "Leo", "Samson", "Elsa", "Cecil"};
const string BEAR_NAMES[10] = {"Yogi", "Smokey", "Paddington", "Lippy", "Bungle", "Baloo", "Rupert", "Winnie the Pooh", "Snuggles", "Bert"};
const string TIGER_NAMES[10] = {"Tony", "Tigger", "Amber", "Cosimia", "Cuddles", "Dave", "Jiba", "Rajah", "Rayas", "Ryker"};


string* parseAnimalData(string data) {
    string* animalData = new string[6];
    stringstream ss(data);
    string temp;

   
    getline(ss, temp, ' ');
    animalData[0] = temp; // age
    getline(ss, temp, ' ');
    animalData[1] = temp; // sex
    getline(ss, temp, ' ');
    animalData[2] = temp; // species
    getline(ss, temp, ',');
    animalData[3] = temp.substr(14); // color
    getline(ss, temp, ',');
    animalData[4] = temp.substr(1); // weight
    getline(ss, temp, ',');
    animalData[5] = temp.substr(5); // origin

    return animalData;
}


string calculateBirthDate() {
    time_t now = time(0);
    tm *ltm = localtime(&now);

    int birthYear = rand() % 4 + ltm->tm_year - 3; // Random year between 3 and 0 years ago
    int birthMonth = rand() % 12 + 1; // Random month
    int birthDay = rand() % 28 + 1; // Random day

    ostringstream oss;
    oss << "birth date " << (birthMonth < 10 ? "0" : "") << birthMonth << "/"
        << (birthDay < 10 ? "0" : "") << birthDay << "/" << birthYear + 1900;

    return oss.str();
}

// Function to create and return a unique animal ID
string create
