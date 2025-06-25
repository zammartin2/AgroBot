# 🐧 Linux Core (Тип 7)

Основной системный демон и служебные модули, работающие на борту UGV-робота (Тип 7 с Linux).

## 📦 Компоненты
| Файл                  | Назначение                         |
|-----------------------|------------------------------------|
| `agrobot_core.py`     | Главный демон, связь с Arduino     |
| `config.yaml`         | Конфигурация портов и логов        |
| `agrobot.service`     | systemd-сервис для автозапуска     |
| `logger/`             | Логи и отладка                     |

## 🔁 Связь
- С Arduino: `Serial` (обычно `/dev/ttyUSB0`)
- С Web UI: HTTP/MQTT (в будущем)
- С сенсорами: напрямую через Python

## 📌 Возможности
- Отправка команд Arduino по UART
- Приём телеметрии от Arduino
- Логирование событий и ошибок
- Состояние бота по команде

## 🚀 Автозапуск
Файл `agrobot.service` устанавливается как systemd-юнит:
```bash
sudo cp agrobot.service /etc/systemd/system/
sudo systemctl daemon-reexec
sudo systemctl enable agrobot
sudo systemctl start agrobot
```

## 🧪 Проверка
```bash
journalctl -u agrobot -f
```

## 🗂 Пример `config.yaml`
```yaml
serial_port: /dev/ttyUSB0
baudrate: 115200
timeout: 1.0
log_file: /var/log/agrobot.log
```
