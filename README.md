A simple request throttler (rate limiter) for Dio, which ensures a minimum
interval between which each request is fired.

## Usage

```dart
// Simple usage
dio.interceptors.add(
  DioThrottler(const Duration(milliseconds: 500)),
);

// Output debug info when throttled
dio.interceptors.add(
  DioThrottler(
    const Duration(milliseconds: 500),
    onThrottled: (req, until) {
      print('${req.uri.toString()} has been delayed until ${until.toString()}');
    },
  ),
);
```

Sample output:

```
flutter: https://www.google.com/ has been delayed until 2023-01-01 12:00:00.123456
flutter: https://www.google.com/ has been delayed until 2023-01-01 12:00:00.623456
flutter: https://www.google.com/ has been delayed until 2023-01-01 12:00:01.123456
flutter: https://www.google.com/ has been delayed until 2023-01-01 12:00:01.623456
flutter: https://www.google.com/ has been delayed until 2023-01-01 12:00:02.123456
```
