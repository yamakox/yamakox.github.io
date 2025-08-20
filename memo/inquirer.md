# python-inquirer - コマンドラインでリストやチェックボックスなどを使えるようにする

- GitHub: [python-inquirer](https://github.com/magmax/python-inquirer)
- [Documentation](https://python-inquirer.readthedocs.io)

## サンプルコード

```main.py
import inquirer

def main():
    questions = [
        inquirer.Text("name", message="What is your name?"),
        inquirer.List('size',
                    message="What size do you need?",
                    choices=['Jumbo', 'Large', 'Standard', 'Medium', 'Small', 'Micro'],
                ),
        inquirer.Checkbox('interests',
                            message="What are you interested in?",
                            choices=['Computers', 'Books', 'Science', 'Nature', 'Fantasy', 'History'],
                            ),
        inquirer.Password('password',
                            message="Enter your password",
                            default="123456",
                            ),
    ]
    answers = inquirer.prompt(questions)
    if answers is None:
        print("No answers provided")
        return
    print(f"Hello, {answers['name']}! You need a {answers['size']} size.")
    print(f"Your interests: {answers['interests']}")
    print(f"Your password: {answers['password']}")

if __name__ == "__main__":
    main()
```

## サンプルプロジェクトの作成

```bash
cd <開発ディレクトリ>
poetry new inquirer-sample
cd inquirer-sample
poetry add inquirer
# pyproject.tomlの[tool.property]に`package-mode = false`を追加
poetry install
eval $(poetry env activate)
python main.py
```
