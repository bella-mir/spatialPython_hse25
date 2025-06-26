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
