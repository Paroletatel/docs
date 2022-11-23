# Таймер, который вызывает контейнер {{ serverless-containers-name }}

_Таймер_ — это [триггер](../trigger/), который запускает [контейнер](../container.md) {{ serverless-containers-name }} по расписанию. Расписание задается в виде [cron-выражения](../../../_includes/functions/cron-expression.md#cron-expression). Время в cron-выражении указывается по [UTC](https://ru.wikipedia.org/wiki/Всемирное_координированное_время).

Таймеру необходим [сервисный аккаунт](../../../iam/concepts/users/service-accounts.md) для вызова контейнера.

{% include [cron-expression](../../../_includes/functions/cron-expression.md) %}

## Роли, необходимые для корректной работы таймера {#roles}

* Для создания таймера вам необходимо разрешение на сервисный аккаунт, от имени которого таймер выполняет операцию. Это разрешение входит в роли [iam.serviceAccounts.user](../../../iam/concepts/access-control/roles.md#sa-user), [editor](../../../iam/concepts/access-control/roles.md#editor) и выше.
* Для работы таймера сервисному аккаунту необходима роль `serverless.containers.invoker` на каталог с контейнером, который вызывает таймер.

Подробнее об [управлении доступом](../../security/index.md).

## Формат сообщения от таймера {#format}

После того как триггер сработает, он отправит в контейнер следующее сообщение: 

{% include [timer-format](../../../_includes/functions/timer-format.md) %}

## См. также {#see-also}

* [Таймер для запуска функции {{ sf-name }}](../../../functions/concepts/trigger/timer.md).