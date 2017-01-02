# totalDays
#just testing stuff

#Initial code for calculating days between two dates using Python. Too much code, but it works.

daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]

def leapYeartest(year): #Self explanatory, tests if a year is a leap year.
  result = False
  if (year%4 == 0):
    result = True
    if (year%100 == 0 and year%400 != 0):
      result = False
  return result

def daysofMonthSum(month1,day1,month2,year1): #Calculates the days from mm1/dd1 up to mm2/yy
  daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31] 
  daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]  
  int_x = month1-1
  int_y = month1-1
  sum = 0
  if leapYeartest(year1) == True:
    daysOfMonths = daysOfMonthsLeap
  while (int_x < month2-1):
      sum = sum + daysOfMonths[int_x]
      int_x+=1
  return sum-day1
#month = 11
#print daysofMonthSum(1,2,3,2012)


#print leapYeartest(2400)

def daysfromBirthday(month1,year1): #Calculates number of days from starting date until end of year
  daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31] 
  month1 = month1-1
  int_x = month1+1
  sum = 0
  if leapYeartest(year1) == True:
    daysOfMonths = daysOfMonthsLeap
  while (int_x < 12):
      sum = sum + daysOfMonths[int_x]
      int_x+=1
  return sum
print daysfromBirthday(6,2011)

def daysuntilToday(month2,year2): #Calculates number of days from start of year until current date
  daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31] 
  if leapYeartest(year2) == True:
    daysOfMonths = daysOfMonthsLeap
  month2 = month2-1
  int_x = 0
  sum = 0
  while (int_x < month2):
      sum = sum + daysOfMonths[int_x]
      int_x+=1
  return sum
#print daysuntilToday(6,2012)

def numberofLeapDays(year1,year2):#Calculates number of leap days between years
  count = 0
  if leapYeartest(year1) == True:
    year1+=4
  while year1 < year2:
    if leapYeartest(year1) == True:
      count+=1
      year1+=4
    else:
      year1+=1
  return count
  
print numberofLeapDays(2011,2012)

def daysBetweenDates(year1, month1, day1, year2, month2, day2): #Final solution.....blegh.
  daysOfMonths = [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  daysOfMonthsLeap = [ 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31] 
  if year1 < year2: #Gets the days if year1 is less than year2
    if leapYeartest(year1) == True:
      daysinMonth1 = daysOfMonthsLeap[month1-1]-day1
    daysinMonth1 = daysOfMonths[month1-1]-day1
    print daysinMonth1
    result = daysfromBirthday(month1,year1) + daysuntilToday(month2,year2) + daysinMonth1 + day2 + numberofLeapDays(year1,year2) + (365*((year2-year1)-1))
  elif month1 != month2: #Gets the days if both years are the same
    result = daysofMonthSum(month1,day1,month2,year1) + day2
  else: #Finally, gets the days if both months/year is same 
    result = day2-day1
  print result  
  
#print daysBetweenDates(2012,3,24,2014,2,26)
