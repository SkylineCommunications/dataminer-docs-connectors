---
uid: Connector_help_Skyline_Booking_Checker
---

# Skyline Booking Checker

## About

The **Skyline Booking Checker** connector counts the number of concurrent SRM bookings scheduled in the system and detects when this number is close to the licensing capacity.

## Key Features

- **SRM license tracking**: Monitors whether an SRM license is available and reports the maximum number of concurrent bookings allowed by that license.
- **Real-time booking load**: Displays the number of bookings currently ongoing.
- **Bookings timeline**: Provides a table displaying how the count of concurrent bookings varies over time.

## Use Cases

### Prevent SRM License Breach

**Challenge**: During periods of high activity, it might not be possible to schedule new bookings because the system has reached the maximum number of bookings allowed by the license.

**Solution**: Use the connector to count the number of current and incoming bookings. The connector will indicate if the current number of booking is close to the maximum allowed number. It will also detect when the license limit might be exceeded.

**Benefit**: Using this connector will reduce SRM license errors when scheduling large numbers of bookings.
