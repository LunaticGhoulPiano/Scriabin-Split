# Ergogen
## 總架構
## 默認參數
- 櫻桃Cherry MX軸
    - ```U```: 19.05 (mm) MX spacing
    - ```u```: 19 (mm) MX spacing
- 凱華Choc矮軸
    - ```cx```: 18 (mm) Choc X spacing
    - ```cy```: 17 (mm) Choc Y spacing
## 常用命名
順序：由上到下，由外到內。
通常根據不同手指有不同命名，並且拇指通常自成一區。當然並非強制要求。
### 2 ~ 5 指
通常命名為```matrix```。
假設是分體式鍵盤的左板，6 columns * 5 rows:
| ROW \ COLUMN     | outer | pinky | ring | middle | index | inner |
| :----------:     | :---: | :---: | :--: | :----: | :---: | :---: |
| **modifiers**    |       |       |      |        |       |       |
| **bottom**       |       |       |      |        |       |       |
| **home**         |       |       |      |        |       |       |
| **top**          |       |       |      |        |       |       |
| **numbers**      |       |       |      |        |       |       |

則

```yaml
points:
  zones:
    matrix:
      columns: # 外到內
        outer:
        pinky:
        ring:
        middle:
        index:
        inner:
      rows: # 上到下
        modifiers:
        bottom:
        home:
        top:
        numbers:
```
### 拇指
通常為```thumb```或```thumb_cluster```。
拇指通常獨立為一區。