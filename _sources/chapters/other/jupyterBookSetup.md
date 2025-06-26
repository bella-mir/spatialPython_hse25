# Интерактивные документы на основе Jupyter Book

## Cоздание и публикация на GitHub Pages

Jupyter Books - прекрасный инструмент, которые предоставляет возможность создавать интерактивные документы/книги/веб-сайты/документацию на основе материалов Jupyter Notebooks и Markdown.

На этой странице вы найдете краткий план, как собрать Jupyter Book и опубликовать его с помощью GitHub Pages

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

Сайт будет в папке `_build/html/`
После этого его можно открыть в браузере (локально)

---

## Часть 2: Публикация на GitHub Pages

### Инициализация git и добавление в GitHub

```bash
git init
git remote add origin https://github.com/USERNAME/REPO.git
git add .
git commit -m "first commit"
git push -u origin main
```

### Установка ghp-import

```bash
pip install ghp-import
```

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
