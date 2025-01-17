# Шардированное копирование

Сервис {{ data-transfer-name }} может задействовать более одного потока исполнения для выполнения трансфера. Функция шардированного копирования позволяет существенно увеличить пропускную способность трансфера, позволяя использовать для трансфера больший объём ресурсов.

Возможности масштабирования ограничены особенностями базы-источника и переносимых данных. Не все источники поддерживают шардированное копирование. Алгоритм распределения данных по нескольким потокам исполнения (алгоритм шардирования) зависит от источника. По этой причине настройки шардированного копирования рекомендуется подбирать для каждого трансфера отдельно.

## Настройки {#settings}

По умолчанию шардированное копирование отключено. Для включения шардированного копирования необходимо задать корректные настройки трансфера.

{% list tabs %}

- Консоль управления


  * **Среда выполнения**

    * **Количество воркеров** — количество виртуальных машин {{ compute-name }}, которые будут задействованы для шардированного копирования. Каждая виртуальная машина имеет собственные ресурсы CPU и RAM и собственное сетевое подключение.

    * **Количество потоков внутри воркера** — максимальное количество потоков исполнения, запускаемых в каждой виртуальной машине.


{% endlist %}
