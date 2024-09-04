# Entropy and Packing Analysis

This Python program is designed to assist in analyzing Windows executable files by calculating entropy, determining entropy levels, and detecting if the executable is packed. The program provides valuable insights for malware analysis and helps identify potential indicators of malicious behavior.

## Motivating Articles and Related Work
Alkhateeb E, Ghorbani A, Habibi Lashkari A. Identifying Malware Packers through Multilayer Feature Engineering in Static Analysis. Information. 2024; 15(2):102. https://doi.org/10.3390/info15020102.

Bermejo Higuera J, Abad Aramburu C, Bermejo Higuera J-R, Sicilia Urban MA, Sicilia Montalvo JA. Systematic Approach to Malware Analysis (SAMA). Applied Sciences. 2020; 10(4):1360. https://doi.org/10.3390/app10041360

OSDev.org PE Ref: https://wiki.osdev.org/PE

## Introduction
Entropy and packing are two important concepts in the context of malware analysis. Entropy measures the randomness or disorder in the distribution of bytes within a file, while packing refers to the process of compressing and obfuscating an executable to make it harder to analyze and reverse engineer. This program combines these concepts to provide insights into the nature of Windows executable files.

## Entropy
Entropy is a measure of the randomness or disorder in the distribution of bytes within a file. It is calculated using Shannon's entropy formula, which quantifies the amount of information or uncertainty in a message. In the context of executable files, entropy can indicate the presence of encrypted, compressed, or obfuscated data.

The program calculates the entropy of the entire executable file and assigns an entropy level based on the following thresholds:
- Low Entropy: Entropy ≤ 5.0
- Medium Entropy: 5.0 < Entropy ≤ 6.5
- High Entropy: Entropy > 6.5

Low entropy suggests a more predictable and less random distribution of bytes, commonly found in executables containing plain text, code, or data without much obfuscation. Medium entropy indicates a moderate level of randomness, typically observed in executables with a mix of plain text, code, and compressed or encrypted data. High entropy implies a highly random and unpredictable distribution of bytes, often associated with encrypted, compressed, or obfuscated data, which is common in packed executables.

## Packing
Packing is a technique used to compress and obfuscate an executable file, making it smaller in size and more difficult to analyze and reverse engineer. Packers, such as UPX (Ultimate Packer for eXecutables), are commonly used for this purpose.

The program checks if the executable is packed by looking for common packer signatures and analyzing the entropy of individual sections within the executable. If the program detects the presence of a packer or finds sections with high entropy, it indicates that the executable is likely packed.

## Results
![Program Output](https://github.com/ericyoc/win_entropy_packing/blob/main/results.jpg)

## Program Functionality
The program performs the following steps:

1. Path to a Windows executable file is provided to upacked Windows executable (e.g., calc.exe).
2. It analyzes the original executable file by calculating its entropy, determining the entropy level, detecting if it is packed, and displaying the section names.
3. It attempts to pack the executable using UPX-UCL, a popular packing tool.
4. If the packing is successful, it analyzes the packed executable file, calculating its entropy, determining the entropy level, and displaying the section names.
5. It provides explanations for the entropy levels and why a packed file may have lower entropy compared to the original file.

## Importance
Analyzing the entropy and packing of executable files is crucial for malware analysis. Here's why:

1. Entropy analysis helps identify executables that may contain encrypted, compressed, or obfuscated data, which are common characteristics of malware. High entropy can be an indicator of potential malicious behavior, as malware authors often employ techniques to conceal their code and evade detection.

2. Detecting packed executables is important because packing is frequently used by malware authors to obstruct analysis and reverse engineering efforts. Packed malware can be more difficult to detect and analyze, as the original code is compressed and obfuscated. By identifying packed executables, cyber analysts can prioritize their analysis efforts and apply appropriate unpacking techniques to reveal the original code.

3. Understanding the entropy levels and packing status of an executable provides valuable insights into its nature and potential risks. Combining this information with other malware analysis techniques, such as static and dynamic analysis, helps cyber analysts make informed decisions about the maliciousness of an executable and develop effective strategies to mitigate threats.

4. The program automates the process of calculating entropy, determining entropy levels, and detecting packing, saving time and effort for cyber analysts. It provides a quick and convenient way to gather initial insights about an executable file before proceeding with more in-depth analysis.

## Disclaimer
It's important to note that while high entropy and packing can be indicators of potential malware, they are not conclusive proof of maliciousness. Legitimate applications may also employ packing for various reasons, such as intellectual property protection or reducing file size. Therefore, the results of this program should be used as part of a comprehensive malware analysis process, combining multiple techniques and considering the overall context of the executable.

Additionally, the program relies on the presence of the UPX-UCL packing tool. If UPX-UCL is not installed or not in the system PATH, the program will display an error message.

Always exercise caution when analyzing and handling potentially malicious files. Make sure to follow proper security practices and use appropriate safeguards, such as running the analysis in an isolated environment.

This repository is intended for educational and research purposes.

## License
Copyright 2024 Eric Yocam

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
