# Selenium_On_Paytm
# You can add your money from bank account to your paytm wallet automatically
# In Python
# Note only if you have account on paytm bank too.
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.remote.webelement import WebElement
from selenium.webdriver.support.ui import Select
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import os
import time

driver = webdriver.Chrome('C://Users//Karan//Desktop//chromedriver')
driver.implicitly_wait(30)
driver.maximize_window()


driver.get("https://paytm.com/paytmwallet")

add=driver.find_element_by_class_name('last')
add.click()
time.sleep(15)
webdriver.ActionChains(driver).send_keys(Keys.ESCAPE).perform()
time.sleep(15)
elem = driver.find_element_by_xpath('//*[@id="site-wrapper"]/menu-user-screens/div/div/div/div[1]/div/ul/li[4]/button')
actions = ActionChains(driver)
actions.click(elem).perform()
time.sleep(10)
#webdriver.ActionChains(driver).send_keys(Keys.ESCAPE).perform()
passcode=driver.find_element_by_xpath('//*[@id="app"]/main/div[2]/div[3]/section[1]/section/div[2]/div/section/div[1]/div[1]/div/div/input')
passcode.send_keys("Your_Password of Paytm bank")

submit=driver.find_element_by_xpath('//*[@id="app"]/main/div[2]/div[3]/section[1]/section/div[2]/div/section/div[1]/div[2]')
submit.click()
show=driver.find_element_by_xpath('//*[@id="user-detail"]/div/div[4]/div[1]/a/div/span[2]/div')
print('Updated Paytm Wallet Balance')
print(show.text)
logout=driver.find_element_by_xpath('//*[@id="user-detail"]/div/div[4]/div[3]/div/div[2]/ul/li[6]/a')
logout.click()

driver.quit()






