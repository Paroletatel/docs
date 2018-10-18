# Назначить роль сервисному аккаунту

Этот раздел про назначение [роли](../../concepts/access-control/roles.md) сервисному аккаунту на какой либо ресурс. Чтобы назначить роль на [сервисный аккаунт](../../concepts/users/service-accounts.md) как на ресурс, воспользуйтесь инструкцией [[!TITLE]](set-access-bindings.md).

Через консоль управления сервисному аккаунту можно назначить роль только на каталог, в котором он был создан. Чтобы назначить ему роль на другой ресурс, используйте CLI или API.

---

**[!TAB Консоль управления]**

Чтобы назначить сервисному аккаунту роль на каталог, в котором он был создан:

1. Выберите каталог.
2. Выберите вкладку **Сервисные аккаунты**.
3. Нажмите значок ![](../../../_assets/dots.svg) напротив сервисного аккаунта и выберите **Редактировать сервисный аккаунт**.
4. Нажмите **Добавить роль** и выберите роль.
5. Нажмите кнопку **Сохранить**.

**[!TAB CLI]**

Чтобы назначить сервисному аккаунту роль на ресурс, выполните команду:

```
yc <SERVICE-NAME> <RESOURCE> add-access-binding <RESOURCE-NAME>|<RESOURCE-ID> \
    --role <ROLE-ID> \
    --subject serviceAccount:<SERVICE-ACCOUNT-ID>
```

где:

* `<SERVICE-NAME>` — имя сервиса, на чей ресурс назначается роль, например `resource-manager`.
* `<RESOURCE>` — категория ресурса, например `cloud`.
* `<RESOURCE-NAME>` — имя ресурса. Вы можете указать ресурс по имени или идентификатору.
* `<RESOURCE-ID>` — идентификатор ресурса.
* `<ROLE-ID>` — идентификатор роли, например `[!KEYREF roles-cloud-owner]`.
* `<SERVICE-ACCOUNT-ID>` — идентификатор сервисного аккаунта, которому назначается роль.

Например, назначьте сервисному аккаунту роль `viewer` на облако `mycloud`:

```
yc resource-manager cloud add-access-binding mycloud \
    --role viewer \
    --subject serviceAccount:ajeptmgeb3f2q56bifci
```

**[!TAB API]**

Чтобы назначить сервисному аккаунту роль на ресурс, воспользуйтесь методом `SetAccessBindings` для того ресурса, на который нужно назначить роль.

---