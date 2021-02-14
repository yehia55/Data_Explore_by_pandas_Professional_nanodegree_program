import pandas as pd
import sys


CITY_DATA = { 'Chicago': 'chicago.csv',
              'New York': 'new_york_city.csv',
              'Washington': 'washington.csv' }
months = ['january', 'february', 'march', 'april', 'may', 'june']
cities=['Chicago','New York','Washington']
days=['Monday',' Tuesday',' Wednesday','Thursday','Friday','Saturday','Sunday']

def load_data(city, month, day):
    
    """
    Loads data for the specified city and filters by month and day if applicable.

    Args:
        (str) city - name of the city to analyze
        (str) month - name of the month to filter by, or "all" to apply no month filter
        (str) day - name of the day of week to filter by, or "all" to apply no day filter
    Returns:
        df - Pandas DataFrame containing city data filtered by month and day
    """

    # load data file into a dataframe
    df = pd.read_csv(CITY_DATA[city])

    # convert the Start Time column to datetime
    df['Start Time'] = pd.to_datetime(df['Start Time'])

    # extract month and day of week from Start Time to create new columns
    df['month'] = df['Start Time'].dt.month
    df['day_of_week'] = df['Start Time'].dt.day_name()

    # filter by month if applicable
    if month != 'all':
        # use the index of the months list to get the corresponding int
        month = months.index(month) + 1

        # filter by month to create the new dataframe
        df = df[df['month'] == month]

    # filter by day of week if applicable
    if day != 'all':
        # filter by day of week to create the new dataframe
        df = df[df['day_of_week'] == day.title()]
    return df



def check (value,reference):
    
    '''check it to check the inputs
        Args:
            (value)the value we want to check
            (reference) the list we will check about the value in 
        return:
            True if value matches one of values in the reference list
            false if the opposite
            '''
    #if key is -1 that means we did not find any match        
    key=-1
    for i in reference:
    #searching loop    
        if value ==i:
            key=1
            break
    return key==1   

def filter_coice (choice):
    '''
    determining the filters we will applicate
    Args:
        (choice) is the inpue the user will enter which 
        determining the type of filter
    return:
        a list contains month value and day value 
        
    '''
    answer=[]#index[0]is for month and index[1]is for day
    if choice == 'month':
        end=''
        while end != 'q':#while loop to handle the wrong input
            print("which month :january,february,march,april,may,june")
            month=input().lower()
            if check(month,months)==False:#check for wrong input
                print('-'*40,"\nwrong input please try again :) \n"+'-'*40)
                continue#will restart the loop if wrong answer
            else:#if right answer will store it in a list to be returned
                answer=[month,'all']
                break
                
    
    elif choice =='day':
        end=''
        while end != 'q':
            print("which day :Monday,Tuesday,Wednesday,Thursday,Friday,Saturday,Sunday")
            day=input().title()
            if check(day,days)==False:
                print('-'*40,"\nwrong input please try again :) \n"+'-'*40)
                continue
            else:
                answer=['all',day] 
                break
        
    elif choice=='both':
        end=''
        while end != 'q':
            print("which month :january,february,march,april,may,june")
            month=input().lower()
            if check(month,months)==False:
                print('-'*40,"\nwrong month input please try again :) \n"+'-'*40)
                continue
            print("which day :Monday,Tuesday,Wednesday,Thursday,Friday,Saturday,Sunday")
            day=input().title()
            if check(day,days)==False:
                print('-'*40,"\nwrong  day input please try again :) \n"+'-'*40)
                continue
            else:
                answer=[month,day] 
                break
    else:
        answer=['all','all']
    return answer    

def display_data(df):
    '''
    a method to display the data five rows by five rows
    Args:
        (df)the data frame we want to display
    return:
        sub data frame contains five rows
    
    '''
    end_loop=''
    while end_loop != 'q':
        print("do you want to display the first 5 rows \n Y for yes and N for no")   
        display_ans=check_and_correct(["Y","N"])
        if display_ans=='N':
            print("ok .. thanks :)")
            break
        counter_start =0
        counter_end=5
        while display_ans=='Y':
            print(df.iloc[counter_start:counter_end])
            print("the next five rows??\n'Y'for yes 'N' for step back")
            display_ans=check_and_correct(["Y","N"])
            counter_start+=5
            counter_end+=5
    

def check_and_correct (reference):
    ''' a method to make sure that the user entered a valid value 
 without affecting the method itself
 Args:
     reference to compare with
 retuen:
     the valid value 
    '''
    key=-1
    while key==-1:
        value=input().upper()
        for i in reference:
            if value==i:
                key=1
                break
        if key==-1:
            print('-'*40,"\nwrong input please try again :) \n"+'-'*40)
            continue
        else:
            break
    return value 

def displaying_statistics(df):
    print('would you like an additional informations?\n Y for yes and N for no')
    additional_cond=check_and_correct(["Y","N"])
    if additional_cond=='Y':
        df['hour']=df['Start Time'].dt.hour
        most_popular_hour=df['hour'].mode()[0]
        user_type=df['User Type'].value_counts()
        most_popular_usre_type=df['User Type'].mode()[0]
        mean_time_duration=df['Trip Duration'].mean()
        most_popular_Start_Station=df['Start Station'].mode()[0]
        most_popular_End_Station=df['End Station'].mode()[0]
        most_popular_gender=df['Gender'].mode()[0]
        #printing the additional details
        print('most popular hour: \n {} \n\n user types:\n {} \n\n most popular user type:\n {} \n\n mean time duration:\n {} \n\n most popular start station:\n {} \n\n most popular end station: \n {} \n\n most popular gender: \n {}'.format(most_popular_hour , user_type , most_popular_usre_type , mean_time_duration , most_popular_Start_Station , most_popular_End_Station , most_popular_gender))
    
def displaying_statistics_washington(df):
    print('would you like an additional informations?\n Y for yes and N for no')
    additional_cond=check_and_correct(["Y","N"])
    if additional_cond=='Y':
        df['hour']=df['Start Time'].dt.hour
        most_popular_hour=df['hour'].mode()[0]
        user_type=df['User Type'].value_counts()
        most_popular_usre_type=df['User Type'].mode()[0]
        mean_time_duration=df['Trip Duration'].mean()
        most_popular_Start_Station=df['Start Station'].mode()[0]
        most_popular_End_Station=df['End Station'].mode()[0]
        #printing the additional details
        print('most popular hour: \n {} \n\n user types:\n {} \n\n most popular user type:\n {} \n\n mean time duration:\n {} \n\n most popular start station:\n {} \n\n most popular end station: \n {}'.format(most_popular_hour , user_type , most_popular_usre_type , mean_time_duration , most_popular_Start_Station , most_popular_End_Station))
        
    
    #main function 
   
# Set an initial value for choice other than the value for 'quit'.
end_the_program =''
# Start a loop that runs until the user enters the value for 'quit'.
while end_the_program != 'q':  
   
    #user interactive part
    print("Hello let's explore some data \n Would you like to start ? \n Y for yes N for no" )
    #making any input is uppercase will reduce errors
    Y_or_N=check_and_correct(["Y","N"])
    if Y_or_N=='N':
        print("ok..thanks :)")
        sys.exit()        
#asking the user to enter the city name and making any input is title will reduce errors too
    print('Would you like to see data for Chicago, New York, or Washington?')
    city=input().title()
#if the input is valid will start the next part  
    if check(city,cities)==False:
        print('-'*40,"\nwrong input please try again :) \n"+'-'*40)
        continue;      

#asking the user to enter the type of filtering and lowercasing all of the input will reduce the error
    print('Would you like to filter the data by month,both,day,or not at all?')
    filter_ans=input().lower()
    if check(filter_ans,['month','day','both','not at all'])==False:
        print('-'*40,"\nwrong input please try again :) \n"+'-'*40)
        continue;    
#if the input is valid will start the next part
    answer=filter_coice(filter_ans)
    df=load_data(city,answer[0],answer[1])
    print(df)
    display_data(df)
    if city == 'Washington':
        displaying_statistics_washington(df)
    else:
        displaying_statistics(df)
    print()
    print('do you want to restart or exit')
    restart_or_exit=check_and_correct(['RESTART','EXIT'])
    if restart_or_exit =='RESTART':
        continue
    else:
        print('thanks .. bye :)')
        break
        
