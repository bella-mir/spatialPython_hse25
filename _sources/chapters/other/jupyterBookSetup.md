# Интерактивные документы на основе Jupyter Book

## Cоздание и публикация на GitHub Pages

Jupyter Books — прекрасный инструмент, который предоставляет возможность создавать интерактивные документы, книги, веб-сайты и документацию на основе Jupyter Notebooks и Markdown.

На этой странице вы найдете краткий план, как собрать Jupyter Book и опубликовать его с помощью GitHub Pages.

---

## Часть 1: Создание книги

### Установка Jupyter Book

```bash
pip install -U jupyter-book
```

---

### Создание книги

```bash
jupyter-book create mybook/
cd mybook/
```

Структура проекта:

- `_config.yml` — настройки книги
- `_toc.yml` — оглавление
- `content/` — главы (в `.md` или `.ipynb`)

---

### Редактирование

Редактируйте или добавляйте свои главы в `content/`.

Пример оглавления (`_toc.yml`):

```yaml
format: jb-book
root: intro
chapters:
  - file: chapter1
  - file: notebooks/my_notebook
```

---

### Сборка HTML-версии

```bash
jupyter-book build .
```

Сайт будет в папке `_build/html/`. После этого его можно открыть в браузере (локально).

---

## Часть 2: Публикация на GitHub Pages

### Настройка Git на компьютере (один раз)

Если вы ещё не использовали Git на этом компьютере — выполните базовую настройку:

```bash
git config --global user.name "Ваше Имя"
git config --global user.email "your_email@example.com"
```

(опционально — настройте SSH-ключ для GitHub)

---

---

### Настройка SSH-ключа для GitHub (опционально)

Если вы не хотите каждый раз вводить логин и пароль при `push/pull`, настройте SSH-доступ:

#### 1. Создайте SSH-ключ (если его нет)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Нажмите Enter, чтобы сохранить в стандартное место (`~/.ssh/id_ed25519`), и при желании задайте пароль.

#### 2. Скопируйте публичный ключ

```bash
cat ~/.ssh/id_ed25519.pub
```

Скопируйте весь вывод.

#### 3. Добавьте ключ в GitHub:

- Перейдите в [https://github.com/settings/keys](https://github.com/settings/keys)
- Нажмите **New SSH key**
- Вставьте ключ и сохраните

#### 4. Проверьте соединение:

```bash
ssh -T git@github.com
```

Если всё настроено правильно, вы увидите приветственное сообщение от GitHub.

Теперь можно клонировать и отправлять изменения через SSH:

```bash
git clone git@github.com:USERNAME/REPO.git
```

### Инициализация git и добавление в GitHub

```bash
git init
git remote add origin https://github.com/USERNAME/REPO.git
git add .
git commit -m "first commit"
git push -u origin main
```

---

### Установка ghp-import

```bash
pip install ghp-import
```

---

### Публикация в ветку `gh-pages`

```bash
ghp-import -n -p -f _build/html
```

---

### Включение GitHub Pages

- Перейдите в настройки репозитория → **Pages**
- Выберите ветку: `gh-pages` и корень (`/`)
- Готово! Сайт будет доступен по адресу:

```
https://USERNAME.github.io/REPO/
```
