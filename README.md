# chinese_lunar_calendar_converter

`chinese_lunar_calendar_converter` 是一个用于公历和农历之间相互转换的 Python 包，并提供万年历打印功能。

## 安装

您可以通过 pip 安装 `chinese_lunar_calendar_converter`：

```bash
pip install chinese_lunar_calendar_converter
```

## 使用示例

### 公历转农历

```python
from chinese_lunar_calendar_converter import solar_to_lunar

gregorian_date = "2025-01-29"
lunar_info = solar_to_lunar(gregorian_date)
print(f"{gregorian_date} 为农历：{lunar_info[0]}年 {lunar_info[1]}月 {lunar_info[2]}日 {lunar_info[3]}{lunar_info[4]}")
# 输出示例: 2025-01-29 为农历：甲辰年 丁丑月 戊戌日 正月初一
```

### 农历转公历

```python
from chinese_lunar_calendar_converter import lunar_to_solar

lunar_year = 2025 # 农历年份
lunar_date_str = "正月初一"
gregorian_info = lunar_to_solar(lunar_year, lunar_date_str)
print(f"农历{lunar_year}年{lunar_date_str} 为公历：{gregorian_info[0]}-{gregorian_info[1]:02d}-{gregorian_info[2]:02d}")
# 输出示例: 农历2025年正月初一 为公历：2025-01-29
```

### 打印万年历

```python
from chinese_lunar_calendar_converter import print_perpetual_calendar

# 打印2024年全年日历
print_perpetual_calendar(2024)

# 打印2024年3月日历
print_perpetual_calendar(2024, 3)
```

## API 接口

### `solar_to_lunar(gregorian_date_str: str) -> Tuple[str, str, str, str, str]`

将公历日期字符串转换为农历日期元组。

*   **参数**:
    *   `gregorian_date_str` (str): 公历日期字符串，格式为 "YYYY-MM-DD"。
*   **返回**:
    *   `Tuple[str, str, str, str, str]`: 包含农历年干支、月干支、日干支、农历月名和农历日名的元组。
        例如: `("甲辰", "丁丑", "戊戌", "正月", "初一")`
*   **可能抛出的异常**:
    *   `ValueError`: 如果输入日期格式不正确或日期无效。

### `lunar_to_solar(lunar_year: int, lunar_date_str: str) -> Tuple[int, int, int]`

将农历日期转换为公历日期元组。

*   **参数**:
    *   `lunar_year` (int): 农历年份（例如：1999）。
    *   `lunar_date_str` (str): 农历日期字符串，格式为 "[闰]月名日名" (例如 "五月十七" 或 "闰五月十七")。也可以是干支日名 (例如 "癸丑日")。
*   **返回**:
    *   `Tuple[int, int, int]`: 包含公历年、月、日的元组。
        例如: `(2025, 1, 29)`
*   **可能抛出的异常**:
    *   `ValueError`: 如果农历日期格式不正确或日期无效。

### `print_perpetual_calendar(year: int, month: int = 0) -> None`

打印指定年份（或月份）的万年历（农历及公历对照）。

*   **参数**:
    *   `year` (int): 公历年份。
    *   `month` (int, optional): 公历月份 (1-12)。如果为 0，则输出全年日历。默认为 0。
*   **可能抛出的异常**:
    *   `ValueError`: 如果年份为 0。

## 贡献

欢迎贡献！如果您有任何建议或发现 bug，请随时提交 issue 或 pull request。

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。
