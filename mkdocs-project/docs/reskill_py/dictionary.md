# ディクショナリ

## 1. ディクショナリとは

ディクショナリ（**辞書型**）は、キーと値のペアを格納するデータ構造です。
リストがインデックスで要素を管理するのに対して、ディクショナリは**任意のキー**（数値、文字列など）を使って、対応する値を格納します。

!!! note "ディクショナリの特徴"

    ディクショナリは、キーと値のペアを管理するため、リストやタプルとは異なる特徴を持っています。

    - 順序は保証されない（Python 3.7以降は挿入順序が保持されますが、基本的に順序に依存しません）
    - キーはユニークでなければならない
    - 値は任意のデータ型（文字列、リスト、数値など）を格納できます

### ディクショナリの作成

__基本的なディクショナリの作成__

ディクショナリは波括弧 `{}` を使って作成します。
また、キーと値はコロン `:` で区切り、複数のペアはコンマ `,` で区切ります。

例えば、以下のように`name`というキーに対して`"Alice"`という値を設定することができます。`"name"`, `"age"`, `"city"` がキーで、`"Alice"`, `30`, `"Tokyo"` がそれぞれ対応する値です。

**プログラム：**
```python
person = {"name": "Alice", "age": 30, "city": "Tokyo"}
print(person)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30, 'city': 'Tokyo'}
```

---

__空のディクショナリの作成__

空のディクショナリも簡単に作成できます。
空のディクショナリは、波括弧 `{}` を使って作成します。

**プログラム：**
```python
empty_dict = {}
print(empty_dict)
```

**出力：**
```bash
{}
```

ディクショナリに後から要素を追加することもできます。

**プログラム：**
```python
empty_dict["name"] = "Alice"
empty_dict["age"] = 30
print(empty_dict)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30}
```

---

__`dict()` を使ってディクショナリを作成__

Pythonには `dict()` という関数もあり、これを使ってディクショナリを作成することもできます。
例えば、以下のようにキーと値をタプルとして渡してディクショナリを作成します。

**プログラム：**
```python
person = dict(name="Alice", age=30, city="Tokyo")
print(person)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30, 'city': 'Tokyo'}
```

---

### ディクショナリの要素の参照

ディクショナリでは、キーを使って対応する値を参照できます。
リストと異なり、ディクショナリはインデックスではなくキーを使ってアクセスするため、非常に柔軟にデータを扱うことができます。
今回は、ディクショナリの要素を参照する方法について学びましょう。

__キーを使って値を取得する__

ディクショナリの要素にアクセスする最も基本的な方法は、キーを使うことです。
キーを指定して、対応する値を取得します。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

print(person["name"])
print(person["age"])
print(person["city"])
```

**出力：**
```bash
Alice
30
Tokyo
```

このように、`person["name"]` という形でキーを指定することで、対応する値を取得できます。
もし、指定したキーが存在しない場合は、KeyError が発生します。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

person['unknown']
```

**出力：**
```bash
---------------------------------------------------------------------------

KeyError                                  Traceback (most recent call last)

/var/folders/lc/k7jt3gx9283453ptp9t9ty5m0000gn/T/ipykernel_26027/3585071311.py in <module>
----> 1 person['unknown']


KeyError: 'unknown'
```

---

__`get()` メソッドを使って値を取得する__

`get()` メソッドを使うと、キーが存在しない場合でもエラーを防ぐことができます。
`get()` メソッドは、キーが見つかった場合は対応する値を返し、見つからなかった場合には指定したデフォルト値（省略すると None）を返します。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

print(person.get("name"))
print(person.get("address", "Not available"))
```

**出力：**
```bash
Alice
Not available
```

`person.get("name")` は、`"name"` に対応する値 `"Alice"` を返します。
`person.get("address", "Not available")` は、`"address"` キーがないため、デフォルトの `"Not available"` を返します。

---

__キーが存在するか確認する (`in` 演算子)__

ディクショナリのキーが存在するかどうかを確認するには、`in` 演算子を使います。
もし指定したキーがディクショナリに存在すれば `True` を、存在しなければ `False` を返します。
これを使えば、キーの存在確認を簡単に行うことができます。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

print("name" in person)
print("address" in person) 
```

**出力：**
```bash
True
False
```

---

__複数の要素を取得する（`items()` メソッド）__

ディクショナリには、キーと値のペアを全て取得するための `items()` メソッドがあります。
`items()` メソッドを使うと、ディクショナリ内のすべてのキーと値をタプルの形で取得できます。
次のように、`for` ループを使ってディクショナリ内のすべてのキーと値を順に参照できます。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

for key, value in person.items():
    print(key, value)
```

**出力：**
```bash
name Alice
age 30
city Tokyo
```

---

__キーのリストを取得する（`keys()` メソッド）__

`keys()` メソッドを使うと、ディクショナリ内のすべてのキーをリストとして取得することができます。
取得されるのは、`dict_keys` という特殊なオブジェクトですが、リストのように扱えます。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

print(person.keys())
print(type(person.keys()))
```

**出力：**
```bash
dict_keys(['name', 'age', 'city'])
<class 'dict_keys'>
```

---

__値のリストを取得する（`values()` メソッド）__

`values()` メソッドを使うと、ディクショナリ内のすべての値をリストとして取得することができます。
これも、`dict_values` というオブジェクトが返されますが、リストのように扱えます。


**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

print(person.values())
print(type(person.values()))
```

**出力：**
```bash
dict_values(['Alice', 30, 'Tokyo'])
<class 'dict_values'>
```

---

__ディクショナリの要素の参照方法のまとめ__

| 操作 | 書き方 | 説明 |
| -- | -- | -- |
| キーを使って値を取得 | `person["name"]` | キーを使って値を取得 |
| `get()` メソッドで値を取得 | `person.get("name")` | `get()` メソッドで値を取得（エラー回避）|
| キーが存在するか確認 (`in` 演算子) | `"name" in person` | キーが存在するか確認 |
| `items()` メソッドで複数の要素を取得 | `person.items()` | キーと値のペアを全て取得 |
| `keys()` メソッドでキーのリストを取得 | `person.keys()` | ディクショナリのキーを取得 |
| `values()` メソッドで値のリストを取得 | `person.values()` | ディクショナリの値を取得 |

---

### ディクショナリの要素の追加と変更

ディクショナリに新しい要素を追加したり、既存の要素の値を変更する方法について解説します。
ディクショナリは、キーと値のペアを管理しているため、簡単に要素を追加・変更できます。

__要素の追加__

ディクショナリに要素を追加するには、新しいキーを指定し、そのキーに対応する値を代入します。
新しいキーを指定すると、そのキーと値のペアがディクショナリに追加されます。
次の例では、`person["city"] = "Tokyo"` という形で新しいキー `"city"` を追加しています。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30
}

person["city"] = "Tokyo"
print(person)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30, 'city': 'Tokyo'}
```

---

__要素の変更__

ディクショナリの要素を変更するには、既存のキーを指定して新しい値を代入します。
もし指定したキーがすでに存在していれば、その値が新しい値に変更されます。
次の例では、`"age"` の値が `30` から `31` に変更されています。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

person["age"] = 31
print(person)
```

**出力；**
```bash
{'name': 'Alice', 'age': 31, 'city': 'Tokyo'}
```

---

__ディクショナリ内での更新（`update()` メソッド）__

複数の要素を同時に追加したり変更したりするには、`update()` メソッドを使います。
`update()` メソッドは、別のディクショナリやキーと値のペアを指定して、ディクショナリを更新することができます。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30
}

person.update({"city": "Tokyo", "age": 31})
print(person)
```

**出力：**
```bash
{'name': 'Alice', 'age': 31, 'city': 'Tokyo'}
```

---

### ディクショナリの要素の削除

ディクショナリから要素を削除する方法について解説します。
ディクショナリでは、キーを使ってそのキーに対応する値を削除できます。

__`del` を使った削除__

`del` を使うことで、指定したキーをディクショナリから削除することができます。
指定したキーが存在しない場合は、`KeyError` が発生します。
次の例では、`"city"` キーを削除しています。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

del person["city"]
print(person)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30}
```

__`pop()` メソッドを使った削除__

`pop()` メソッドを使うことで、指定したキーに対応する値を削除すると同時に、その値を返すことができます。
`pop()` メソッドを使うと、削除した値を取得できるため、削除した値が必要な場合に便利です。
次の例では、`pop("age")` で `"age"` キーを削除し、削除した値 `30` を返しています。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

age = person.pop("age")

print(person)
print(age)
```

**出力：**
```bash
{'name': 'Alice', 'city': 'Tokyo'}
30
```

__`popitem()` メソッドを使った削除__

`popitem()` メソッドを使うと、ディクショナリから最後の要素（キーと値のペア）を削除することができます。
これも削除したペアを返します。
次の例では、ディクショナリの最後の要素（`"city": "Tokyo"`) を削除し、そのペアがタプルとして返されています。

**プログラム：**
```python
person = {
    "name": "Alice",
    "age": 30,
    "city": "Tokyo"
}

item = person.popitem()

print(person)
print(item)
```

**出力：**
```bash
{'name': 'Alice', 'age': 30}
('city', 'Tokyo')
```

---

### ディクショナリ要素の追加・変更・削除のまとめ

| 操作 | 書き方 | 説明 |
| -- | -- | -- |
| 要素の追加 | `person["city"] = "Tokyo"`| 新しいキーと値のペアを追加 |
| 要素の変更 | `person["age"] = 31` | 既存のキーの値を変更 |
| 複数の要素を追加・変更 | `person.update({"city": "Tokyo", "age": 31})` | update() メソッドで複数の要素を一度に変更・追加 |
| `del` を使った削除 | `del person["city"]` | 指定したキーと対応する値を削除 |
| `pop()` メソッドを使った削除 | `person.pop("age")` | 指定したキーを削除し、その値を返す |
| `popitem()` メソッドを使った削除 | `person.popitem()` | 最後の要素（キーと値のペア）を削除し、そのペアを返す |

## 2. ディクショナリとリストの比較
リストとディクショナリは、どちらもデータを格納するためのコンテナですが、それぞれの特徴にはいくつかの違いがあります。
ここでは、リストとディクショナリを比較し、それぞれの適した使い方を理解しましょう。

!!! note "1. データの格納方法"

    リストは、 インデックス（順番）を使ってデータを格納します。
    リストの要素は順番が重要で、インデックス番号（`0`, `1`, `2`, ...）でアクセスします。

    ディクショナリは、キーと値のペアでデータを格納します。
    ディクショナリではキーを使ってデータにアクセスしますが、順番は基本的に関係ありません（Python 3.7以降、挿入順序が保持されますが、それでも順番よりキーの意味が重要です）。

!!! note "2. データへのアクセス方法"

    リストは、インデックス番号を使って要素にアクセスします。
    インデックスは整数であり、順番に依存しています。

    ディクショナリは、キーを使って値にアクセスします。
    キーは任意の **不変の型（文字列、整数、タプルなど）** であり、順番に依存せず、キーで明示的に指定して値を取得します。

!!! note "3. データの順序"

    リストは、要素が順番通り格納されます。
    インデックス番号に基づいて要素が並べられているため、順番が重要です。

    ディクショナリは、Python 3.7以降、挿入順序は保持されますが、順番に依存しません。
    ディクショナリでは、キーによって値にアクセスするため、順番に意味を持たせることは少ないです。

!!! note "4. データの格納目的"

    リストは、順序付きのデータが必要な場合に適しています。
    同じ種類のデータを順番に格納したい場合に便利です。例えば、商品リストや名前のリストなど。

    ディクショナリは、キーを使って特定のデータを迅速に取り出したい場合に適しています。
    名前と年齢、IDと名前など、キーと値の対応を持つデータを扱いたい場合に使います。

!!! note "5. メモリ効率"

    リストは、順番に格納されたデータを扱うため、インデックスを使って要素にアクセスできますが、キーを使ってデータを探すことはできません。
    リストはメモリ的に効率的で、順番通りに要素を格納するシンプルなデータ構造です。

    ディクショナリは、キーと値のペアを格納するため、アクセスが高速ですが、キーに対するハッシュを使うため、リストよりもメモリを多く消費する場合があります。
    ディクショナリは、キーに基づいてデータを高速に検索できるため、大規模なデータに対して有効です。

__まとめ__

リストは、順序が重要なデータを扱うのに適しており、ディクショナリはキーと値の対応が重要なデータに適しています。それぞれの特徴を理解し、使い分けることで、より効果的にデータを管理できるようになります。
次の表を参考に、リストとディクショナリを使い分けてデータを管理する方法を理解しましょう。

| 特徴                   | リスト                          | ディクショナリ                    |
|:-|:-|:-|
| 1. データの格納方法       | 順番に格納、インデックスを使用     | キーと値のペア、キーを使用       |
| 2. データのアクセス方法   | インデックス番号を使用            | キーを使用                       |
| 3. データの順序           | 順番通り（インデックス順）         | 挿入順序（Python 3.7以降）       |
| 4. 使用目的               | 順序を保持したデータの管理          | キーと値のペアで特定のデータを管理 |
| 5. メモリ効率             | 効率的（順番通りのデータ）         | キーと値にハッシュテーブルを使用  |

---

## 3. コンテナの応用

### コンテナの相互変換

Pythonでは、リスト（`list`）、タプル（`tuple`）、セット（`set`）、ディクショナリ（`dict`） などのコンテナ同士を相互に変換することができます。
データの特性に応じて適切なコンテナを選択し、柔軟に使い分けるために重要なテクニックです。

---

__1. リスト ⇔ タプル の変換__

リストとタプルは、`list()` や `tuple()` を使って簡単に変換できます。

使い分け：

- リスト は変更可能（ミュータブル）で、データの追加・削除ができる
- タプル は変更不可（イミュータブル）で、安全性が高い

**プログラム：**
```python
# リスト → タプル
numbers_list = [1, 2, 3]
numbers_tuple = tuple(numbers_list)
print(numbers_tuple)

# タプル → リスト
numbers_tuple = (4, 5, 6)
numbers_list = list(numbers_tuple)
print(numbers_list)
```

**出力：**
```bash
(1, 2, 3)
[4, 5, 6]
```

---

__2. リスト ⇔ セット の変換__

セットに変換すると重複が自動的に削除されます。

使い分け:

- リスト は順序を保持するが、重複を許す
- セット は順序を保持しないが、重複を削除する

**プログラム：**
```python
# リスト → セット（重複削除）
numbers_list = [1, 2, 2, 3, 4, 4, 5]
numbers_set = set(numbers_list)
print(numbers_set)

# セット → リスト（順序がなくなる可能性あり）
numbers_list = list(numbers_set)
print(numbers_list) 
```

**出力：**
```bash
{1, 2, 3, 4, 5}
[1, 2, 3, 4, 5]
```

---

__3. リスト ⇔ ディクショナリ の変換__

リストとディクショナリは構造が異なるため、リストをキーと値のペアに変換する必要があります。

使い分け:

- リスト は単純なデータの並びに適している
- ディクショナリ はキーと値の関係を管理するのに適している


**プログラム：**
```python
# リスト（タプルのリスト） → ディクショナリ
pairs = [("apple", 100), ("banana", 200), ("cherry", 300)]
fruits_dict = dict(pairs)
print(fruits_dict)

# ディクショナリ → リスト（キーや値のリストに）
keys_list = list(fruits_dict.keys())
values_list = list(fruits_dict.values())

print(keys_list)
print(values_list)
```

**出力：**
```bash
{'apple': 100, 'banana': 200, 'cherry': 300}
['apple', 'banana', 'cherry']
[100, 200, 300]
```

---

__コンテナの相互変換のまとめ__

コンテナの相互変換を活用することで、データを適切な形に整え、効率的に処理できます。

| **変換元** → **変換先** | **変換方法** |
|:-|:-:|
| リスト → タプル | `tuple(list_data)` |
| タプル → リスト | `list(tuple_data)` |
| リスト → セット | `set(list_data)` |
| セット → リスト | `list(set_data)` |
| リスト → 辞書 | `dict(list_of_tuples)` |
| 辞書 → リスト（キー） | `list(dict.keys())` |
| 辞書 → リスト（値） | `list(dict.values())` |

---

### コンテナのネスト

コンテナのネスト（入れ子） とは、リストの中にリストを入れる、ディクショナリの中にリストを入れる など、
異なるデータ構造を組み合わせて使うことを指します。
ネストを活用することで、より複雑なデータを整理・管理しやすくなります。

__1. リストのネスト__

リストの中にリストを含めると、2次元リスト（リストのリスト） を作ることができます。

**プログラム：**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matrix[0])
print(matrix[0][1])
```

**出力：**
```bash
[1, 2, 3]
2
```

!!! note "応用"
    リストのリストを使うことで、表（テーブル）データ を扱えます。

    ```python
    students = [
        ["Alice", 85, 90, 88], 
        ["Bob", 78, 92, 80], 
        ["Charlie", 90, 85, 95]
    ]

    # Bobの2つ目の点数を取得
    print(students[1][2])  # 92
    ```

---

__2. ディクショナリのネスト__

ディクショナリの中にリストや別のディクショナリを入れることで、
データをより意味のある形で整理 できます。

**プログラム：**
```python
student_scores = {
    "Alice": {"math": 85, "english": 90, "science": 88},
    "Bob": {"math": 78, "english": 92, "science": 80},
    "Charlie": {"math": 90, "english": 85, "science": 95}
}

print(student_scores["Bob"]["english"])
```

**出力：**
```bash
92
```

!!! note "応用"
    辞書をリストに入れることで、複数のデータを扱いやすく なります。

    ```python
    employees = [
        {"name": "Alice", "age": 25, "department": "HR"},
        {"name": "Bob", "age": 30, "department": "IT"},
        {"name": "Charlie", "age": 28, "department": "Finance"}
    ]

    # Bobの部署を取得
    print(employees[1]["department"])  # IT
    ```

__3. セットのネスト__

セットはネストできない（リストや辞書のように入れ子にできない）ため、
セットの中にセットを入れることはできません。セットは「変更できない（ミュータブル）データ型」を要素として持てないため、セットの中にセットを入れることは不可能となっています

**プログラム：**
```python
set_a = {1, 2, {3, 4}}  # エラー
```

**出力：**
```bash
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

/var/folders/lc/k7jt3gx9283453ptp9t9ty5m0000gn/T/ipykernel_26027/1420277885.py in <module>
----> 1 set_a = {1, 2, {3, 4}}  # エラー


TypeError: unhashable type: 'set'
```

---

__4. ネストしたデータのアクセス__

ネストしたコンテナのデータにアクセスするときは、インデックスやキーを順に指定 します。

**プログラム：**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(matrix[1][2])

student_scores = {
    "Alice": {"math": 85, "english": 90},
    "Bob": {"math": 78, "english": 92}
}
print(student_scores["Alice"]["math"])
```

**出力：**
```bash
6
85
```

---

## この章のまとめ

本章では、データを整理・管理するための「コンテナ」について学びました。

!!! success "1. 変数が持つ不便さ"

    - 変数は1つの値しか保持できず、多くのデータを扱うのに不便。
    - より効率的なデータ管理のために「リスト」「ディクショナリ」「タプル」「セット」といったコンテナを活用する。

!!! success "2. リスト"

    - 特徴: 複数の要素を順番に保持でき、変更が可能。
    - 作成: `[]` を使ってリストを作成。
    - 要素の参照: インデックスを使ってアクセス。
    - 合計と要素数の取得: `sum()` や `len()` を利用。
    - 追加・削除・変更: `append()`, `remove()`,` insert()` などのメソッドを使用。
    - 高度な指定: スライスで部分的に取り出しや更新が可能。

!!! success "3. ディクショナリ"

    - 特徴: キーと値のペアでデータを管理し、高速にアクセス可能。
    - 作成: `{}` を使ってキーと値を定義。
    - 要素の参照: `dict[key]` で値を取得。
    - 追加・変更: `dict[key] = value` で設定。
    - 削除: `del dict[key]` で削除。
    - リストとの比較: ディクショナリはキーを利用するため、リストよりも検索が高速な場合がある。

!!! success "4. タプルとセット"

    - タプル: `()` で定義し、変更不可（イミュータブル）。リストより安全にデータを保持できる。
    - セット: `{}` で定義し、重複を許さない。集合演算が可能。

!!! success "5. コンテナの応用"

    - 相互変換: `list()`, `tuple()`, `set()`, `dict()` を使ってコンテナ間の変換が可能。
    - ネスト: コンテナの中に別のコンテナを入れることで複雑なデータ構造を管理。

これらのコンテナを適切に活用することで、プログラムのデータ管理がより柔軟かつ効率的になります。

---

👉 [次の章では、**条件分岐** について学び、より実用的なプログラムを作成していきましょう！](conditinal_statement.md)