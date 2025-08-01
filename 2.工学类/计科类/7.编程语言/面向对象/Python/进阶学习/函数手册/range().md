Python 的 `range()` 函数是一个内置函数，用于生成一个**不可变的整数序列**，常用于循环控制（如 `for` 循环）或需要整数列表的场景。以下是其核心特性和用法：

### 1. **基本功能**
- `range()` 可以创建从指定起点到终点的连续整数序列（默认步长为1），但**不包含终止值**。例如：
  ```python
  for x in range(5):
      print(x)  # 输出 0,1,2,3,4
  ```
  这里生成了从0开始、到4结束的整数序列。

### 2. **参数说明**
- `range()` 支持三种参数形式：
  - `range(stop)`：默认从0开始，步长为1，生成 `[0, stop)` 的整数。
  - `range(start, stop)`：从 `start` 开始，步长为1，生成 `[start, stop)` 的整数。
  - `range(start, stop, step)`：自定义步长 `step`（可为负数），生成 `[start, stop)` 区间内按步长递增或递减的整数。
  示例：
  ```python
  list(range(1, 5))    # [1, 2, 3, 4]
  list(range(0, 10, 2)) # [0, 2, 4, 6, 8]
  ```

### 3. **特性**
- **惰性求值**：`range()` 返回的是一个可迭代对象（非列表），仅在迭代时按需生成值，节省内存。
- **不可变性**：生成的整数序列是固定的，无法直接修改其内容。

### 4. **应用场景**
- **循环控制**：最常见的用途是在 `for` 循环中指定迭代次数或索引范围。
- **生成整数列表**：通过 `list(range(...))` 快速创建整数列表。
- **反向遍历**：通过负数步长实现逆序生成，例如 `range(5, 0, -1)` 生成 `[5,4,3,2,1]`。

### 5. **注意事项**
- 在 Python 3 中，`range()` 的行为与 Python 2 的 `xrange()` 类似，均是惰性生成；而 Python 2 的 `range()` 会直接生成完整列表。

通过灵活组合参数和步长，`range()` 能高效处理各种需要整数序列的场景，是 Python 中简化循环逻辑的重要工具。