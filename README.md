<div align="center">

# Dota2 Match Outcome Prediction

[![PyTorch](https://img.shields.io/badge/PyTorch-ee4c2c?logo=pytorch&logoColor=white)](https://pytorch.org/get-started/locally/)
[![Lightning](https://img.shields.io/badge/-Lightning-792ee5?logo=pytorchlightning&logoColor=white)](https://pytorchlightning.ai/)
[![Hydra](https://img.shields.io/badge/Config-Hydra-89b8cd)](https://hydra.cc/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?labelColor=gray)](/LICENSE)

Прогнозирование исхода матчей **Dota 2**

</div>

---

##  Описание

Проект позволяет предсказывать победителя матча в **Dota 2** на основе игровых данных (составы команд, статистика игроков, предметы, герои).  

Основные возможности:  

- Использование нескольких моделей на выбор (например, Dense, Transformer, GNN)  
- Гибкая настройка экспериментов через Hydra  
- Легкая интеграция логгеров: TensorBoard, CSVLogger, W&B  
- Поддержка CPU, GPU и мульти-GPU обучения  
- Контроль версий экспериментов и логирование метрик  

---

##  Особенности

- Быстрая настройка новых моделей и конфигураций  
- Минимум «шаблонного» кода для обучения и оценки  
- Поддержка гиперпараметрических поисков через Hydra multirun и Optuna  
- Сохранение контрольных точек и возможность возобновления обучения  
- Встроенные утилиты для анализа результатов  

---

##  Установка

#### Через Pip

```bash
# Клонируем репозиторий
git clone https://github.com/YourGithubName/dota2-prediction
cd dota2-prediction

# Создаем виртуальное окружение
python -m venv .venv
source .venv/bin/activate   # Linux/macOS
.venv\Scripts\activate      # Windows

# Устанавливаем зависимости
pip install -r requirements.txt
```
#### Через Conda

```bash
# Клонируем репозиторий
git clone https://github.com/YourGithubName/dota2-prediction
cd dota2-prediction

# Создаем окружение из environment.yaml
conda env create -f environment.yaml -n dota2env
conda activate dota2env
```

## Запуск обучения
```bash
# Обучение на CPU
python src/train.py trainer=cpu

# Обучение на GPU
python src/train.py trainer=gpu
```
### Выбор модели и эксперимента:
```bash
# Используем эксперимент с определенной моделью
python src/train.py experiment=example.yaml
```

### Переопределение параметров через командную строку:
```bash
python src/train.py trainer.max_epochs=20 data.batch_size=64 model.optimizer.lr=0.001 model.name=Transformer
```

## Логирование

По умолчанию все логи сохраняются в папку logs/:

```bash
logs/
├── task_name/
│   ├── runs/            # Логи отдельных запусков
│   └── multiruns/       # Логи мультизапусков
└── debugs/              # Логи для режима отладки
```
Можно выбирать логгер в configs/logger/ (CSVLogger, TensorBoard, W&B).

## Лицензия
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)
