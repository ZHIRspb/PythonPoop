# Coloured data function

```python
colour_tmp_list = {
               87: ['-19', '-18', '-17', '-16', '-15'],
               123: ['-14', '-13', '-12', '-11', '-10'],
               159: ['-9', '-8', '-7', '-6', '-5'],
               195: ['-4', '-3', '-2', '-1'],
               231: ['0'],
               230: ['1', '2', '3', '4', '5'],
               229: ['6', '7', '8', '9', '10'],
               228: ['11', '12', '13', '14', '15', '16', '17', '18'],
               227: ['19', '20', '21', '22', '23', '24', '25', '26'],
               }


def colored_tmp(data):
    for key, value in colour_tmp_list.items():
        if str(data) in value:
            colored_data = f"\033[38;5;{key}m{str(data)}\033[0;0m"

        elif data > 26:
            colored_data = f"\033[38;5;196m{str(data)}\033[0;0m"

        elif data < -19:
            colored_data = f"\033[38;5;57m{str(data)}\033[0;0m"
        else:
            continue
        return colored_data


colour_wind_list = {231: ['0', '1'],
                    123: ['2', '3', '4'],
                    45: ['5', '6', '7', '8'],
                    39: ['9', '10', '11', '12', '13'],
                    31: ['14', '15', '16', '17', '18'],
                    24: ['19', '20', '21', '22', '23'],
                    }


def colored_wind(data):
    for key, value in colour_wind_list.items():
        if str(int(data)) in value:
            colored_data = f"\033[38;5;{key}m{str(data)}\033[0;0m"
        elif int(data) > 23:
            colored_data = f"\033[38;5;18m{str(data)}\033[0;0m"
        else:
            continue
        return colored_data
```
