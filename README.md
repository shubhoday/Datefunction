# Datefunction
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace dayFinder
{
    class DateFunction
    {
        int day = 0;
        int day1 = 0;
        int month1 = 0;
        int year1 =0;
        int day2 = 0; 
        int month2 = 0;
        int year2 = 0;
        public static Boolean isLeapYear(int year) {
            return (year % 4 == 0);
        }
        
        public int getDays(uDate date1, uDate date2){
            //date1.show(date1);
            day1 = date1.getDay();
            month1 = date1.getMonth();
            year1 = date1.getYear();
            day2 = date2.getDay();
            month2 = date2.getMonth();
            year2 = date2.getYear();
            day = GetDifference();
            
            return day;
        }
        public int GetDifference(){
            while (IsDate1BeforeDate2())
            {
                //Console.WriteLine(day);
                day++;
                IncreaseDateByOneDay();
            }

            return day;
        }
        public bool IsDate1BeforeDate2()
        {
            if (year1 < year2){
                return true;
            }
            else {
                if (month1 < month2)
                {
                    return true;
                }
                else{
                    if (day1 < day2)
                    {
                        return true;
                    }
                    else {
                        return false;
                    }
                }
            }
            
        }
        public bool IsLastMonthInYear(int month) { 
            return (month == 12);
        }
        public void IncreaseDateByOneDay(){
            if (IsLastDayInMonth()){
                if (IsLastMonthInYear(month1)){
                    month1 = 1;
                    day1 = 1;
                    year1++;
                }
                else{
                    day1 = 1;
                    month1++;
                }
            }
            else{
                day1++;
            }
        }
        public bool IsLastDayInMonth(){ 
            int[] daysPerMonth = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
            int[] daysPerMonthLeapYear = { 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
            if (isLeapYear(year1)){
                return (daysPerMonthLeapYear[month1 - 1] == day1);
            }
            else{
                return (daysPerMonth[month1 - 1] == day1);
            }
        }
    }
}
