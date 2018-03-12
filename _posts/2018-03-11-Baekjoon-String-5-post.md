---

layout: post

title: 1316. 그룹 단어 체커

categories: [string]

---

```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;

bool check_char(char check, string input, int num) {
	for (int i = 0; i < input.length(); i++) {
		if (check == input[i] && abs(num - i) <= 1)
			num = i;
		else if (check == input[i] && abs(num - i) > 1) {
			for (int j = i; j < num; j++) {
				if(input[j] != check)
					return false;
			}
		}
	}
	return true;
}


int main() {
	int size;
	vector<string> vector;
	string input;
	char check;
	bool result;
	int count = 0;

	cin >> size;
	if (size > 100)
		exit(0);
	else {
		vector.reserve(size);
		for (int i = 0; i < size; i++) {
			cin >> input;
			if (input.length() > 100)
				exit(0);
			else
				vector.push_back(input);
		}

		for (int i = 0; i < vector.size(); i++) {
			for (int j = 0; j < vector[i].length(); j++) {
				check = vector[i].at(j);
				result = check_char(check, vector[i], j);
				if (result == false)
					break;
			}
			if(result == true)
				count++;
		}
		printf("%d", count);
	}
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}