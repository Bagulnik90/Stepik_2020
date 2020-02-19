from selenium.webdriver.chrome.webdriver import WebDriver
import math


# ����������� ������� ��� �������� ��������
def calc(x):
    return str(math.log(abs(12 * math.sin(int(x)))))


# ��������� �������
con = WebDriver()

# ��������� ������� ��������
con.get("http://suninjuly.github.io/math.html")

# ������� ���-������� x
web_element_x = con.find_element_by_css_selector("#input_value")

# ��������� �������� �������� x
x_int = int(web_element_x.text)

# ������� �������� ��� �����
value = calc(x_int)

# ������� �������� ��������� ����, �������, �����-������, ������ "���������"
text_field = con.find_element_by_css_selector("#answer")
checkbox = con.find_element_by_css_selector("#robotCheckbox")
radio_btn = con.find_element_by_css_selector("#robotsRule")
submit_btn = con.find_element_by_css_selector('[type="submit"]')

# ������ �������� � ��������� ����
text_field.send_keys(value)

# �������� �������
checkbox.click()

# �������� �������� �����-������
radio_btn.click()

# �������� �� ������ "���������"
submit_btn.click()

# ��������� �������
con.quit()