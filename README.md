# totalDays
#just testing stuff

#Updated code for calculating the number of days between two dates in Python. Followed suggestions from Udacity instructor.

def leapYeartest(year): #Leap year test...
  result = False
  if (year%4 == 0):
    result = True
    if (year%100 == 0 and year%400 != 0):
      result = False
  return result
  
  
def daysInMonth(year,month): #Just returns days in the given month(+1 to feb if leap year)
  daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  if leapYeartest(year):
    return daysOfMonthsLeap[month-1]
  return daysOfMonths[month-1]
  
#print daysInMonth(2016,12)

def nextDay(year, month, day): #Returns the date of following day
    if day < daysInMonth(year,month):
        return year, month, day + 1
    else:
        if month == 12:
            return year + 1, 1, 1
        else:
            return year, month + 1, 1


def areDatesEqual(Date1,Date2):
    return Date1 == Date2

Date1 = (2012, 1, 2)
Date2 = (2012, 1, 2)
#print areDatesEqual(Date1,Date2)


        
def daysBetweenDates(year1, month1, day1, year2, month2, day2): #final procedure
    """Returns the number of days between year1/month1/day1
       and year2/month2/day2. Assumes inputs are valid dates
       in Gregorian calendar, and the first date is not after
       the second."""
        
    # YOUR CODE HERE!
    numberofdays = 0
    Date1 = (year1, month1, day1)
    Date2 = (year2, month2, day2)
    assert Date1 < Date2 #Makes sure input is valid
    while areDatesEqual(Date1,Date2) == False: #Adds up all the days until current date is reached
        nextDay(year1, month1, day1)
        year1,month1,day1 = nextDay(year1, month1, day1)
        Date1 = year1,month1,day1
        numberofdays+=1
        #print nextDay(year1,month1,day1)
    return numberofdays 
print daysBetweenDates(1900,1,1,1999,1,1) 
  
#print daysBetweenDates(2012,3,24,2014,2,26)
