try:
    current_hour = int(input("Enter an hour between 1 and 12: "))

    if current_hour < 1 or current_hour > 12:
        print("Invalid input. Please enter an hour between 1 and 12.")
    else:
        period = int(input("Enter 1 for am and 2 for pm: "))

        if period != 1 and period != 2:
            print("Invalid Input. Please enter 1 for am or 2 for pm. ")
        else:
            hours_into_future = int(input("Enter the number of hours to advance into the future: "))

            if hours_into_future < 12:
                total_hours = (current_hour + hours_into_future) % 12
                future_hour = total_hours if total_hours != 0 else 12
                if period == 1:
                    future_period = "PM"
                else:
                    future_period = "AM"

            elif hours_into_future > 12:
                total_hours = (current_hour + hours_into_future)
                future_hour = total_hours % 12
                if future_hour == 0:
                    future_hour = 12
                    if total_hours >= 24 and period == 1:
                        future_period = "AM"
                    else:
                        total_hours = (current_hour + hours_into_future) % 12
                        future_hour = total_hours if total_hours != 0 else 12
                        future_period = 'PM'
                else:
                    future_period = 'AM'
            else:
                total_hours = (current_hour + hours_into_future) % 12
                future_hour = total_hours if total_hours != 0 else 12
                future_period = "AM" if period == 2 else "PM"

            print(f"{future_hour} {future_period}")

except ValueError:
    print("Invalid Input.")
