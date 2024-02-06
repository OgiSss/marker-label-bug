# Google Maps Marker Memory Leak

## Introduction

This project demonstrates a specific issue encountered when using Google Maps in conjunction with the Angular framework, specifically within the angular/google-maps library. The issue arises under conditions where a large number of markers (approximately 4,000 or more) are rendered on the map with labels attached to each marker. Under these circumstances, an unexpected memory leak occurs, potentially degrading performance and user experience.

## Problem Description

The application uses Google Maps to render a significant number of markers, a common requirement for projects needing to display dense geographical data (my client forced it and he didn't want to have clusters and i coudn't persuaded him). Each marker is assigned a label to provide additional information to the user. However, when the number of labeled markers reaches a high threshold, a memory leak is observed. This leak can lead to increased memory usage over time, which leads to crash the browser.

## Reproducing the Issue

This project contains a simple setup to reproduce the memory leak issue:

1. **Google Maps Setup**: Initialization of a Google Maps instance within an Angular application.
2. **Marker Rendering**: Dynamically generating and rendering around 4,000 markers with labels on the map.
3. **Memory Leak Observation**: Tools and methods to observe the memory usage and identify the leak.

To replicate the problem, follow the steps outlined in the **Installation** and **Usage** sections.

## Installation

1. Clone this repository to your local machine.
2. You have to provide your own key! In index.html you will find placeholder YOUR_API_KEY. Replace it with you key
3. Navigate to the project directory and install the necessary dependencies by running `npm install`.
4. Start the application using `npm start`. This will launch the app on your default web browser.

## Usage

To observe the memory leak:

1. Open the application as instructed in the **Installation** section.
2. Uncomment BROKEN SECTION and comment previous section
3. Use your browser's developer tools to monitor memory usage while the application is running.
4. Notice the increase in memory usage over time, indicating a memory leak.

## Technical Details

- **Framework**: Angular
- **Library**: angular/google-maps
- **Issue**: Memory leak when rendering a large number of markers with labels.

## Potential Solutions

This project highlights a significant issue when rendering a large number of markers with labels using the angular/google-maps library. The core of the problem lies in the use of basic markers, which, when labels are added, leads to a memory leak, adversely affecting performance. Google Maps provides an option for advanced markers, designed to handle such use cases more efficiently, mitigating the risk of memory leaks.

### Advanced Markers as a Solution

The ideal solution involves leveraging these advanced markers, which offer optimized performance and are better suited for handling a large number of markers with labels. Unfortunately, the current version of the angular/google-maps library does not support these advanced markers, limiting the ability to utilize this efficient functionality within Angular projects.

Pull request: https://github.com/angular/components/pull/28525

### Contributing to the Angular Google Maps Library

Recognizing this limitation, I have initiated a contribution to the angular/google-maps library to incorporate support for advanced markers. This contribution is detailed in a pull request submitted to the Angular component project's GitHub repository. By integrating advanced markers into the library, we can provide a robust solution to the memory leak issue, enabling developers to utilize Google Maps in their Angular applications more effectively and efficiently.

This pull request represents a significant step towards improving the angular/google-maps library's functionality, making it more versatile and suitable for complex applications requiring the rendering of a large number of markers with labels.

### Workarounds and Interim Solutions

Until the pull request is reviewed and potentially merged, developers facing this issue might consider several workarounds:

1. **Optimizing Marker Usage**: Limit the number of markers with labels rendered simultaneously, or implement marker clustering to reduce memory consumption.
2. **Custom Marker Implementation**: Explore custom implementations that mimic the behavior of advanced markers using available Angular and Google Maps APIs.
3. **Alternative Libraries**: Evaluate other libraries or frameworks that support advanced markers and can be integrated into Angular projects.

These interim solutions can mitigate the issue but may not offer the same level of efficiency and ease of use as the proposed integration of advanced markers into the angular/google-maps library.

## License

MIT
