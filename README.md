# OSTROV — passenger app foundation

Первый более цельный Flutter-прототип пассажирского приложения OSTROV для Южно-Сахалинска.

## Реализовано в исходниках
- Брендовая тема OSTROV: небесно-голубой и белый.
- OSM-карта с атрибуцией.
- Поиск адресов Photon с debounce и фильтром примерной зоны города.
- Обратное геокодирование при выборе точки на карте.
- GPS через Geolocator с обработкой отказа в разрешении.
- Построение автомобильного маршрута через OSRM demo API.
- Отображение геометрии, расстояния и примерного времени маршрута.
- Выбор тарифного класса и наличной/карточной оплаты.
- Заказ пока заканчивается прозрачным экраном-подтверждением, а не фиктивной отправкой водителю.

## Честный статус
Это клиентский прототип, не готовый коммерческий агрегатор и не APK/AAB. В этой среде Flutter SDK и Android SDK отсутствуют, поэтому реальная компиляция и `flutter analyze` не выполнялись. В исходниках не заявляется, что приложение прошло сборку.

## Быстрый старт
```bash
flutter create --org ru.ostrov --project-name taxi --platforms=android,ios ostrov
# Перенести папки lib/ и test/, а также зависимости из pubspec.yaml.
# Затем объединить Android permissions из android/app/src/main/AndroidManifest.xml
# и добавить ключ из ios/Runner/Info.plist.fragment в настоящий Info.plist.
flutter pub get
flutter analyze
flutter test
flutter run
```

## Важные production-замены
Публичные `tile.openstreetmap.org`, Photon demo и OSRM demo — только прототипные endpoints. Перед коммерческим запуском заменить их на контрактные/самостоятельно размещённые сервисы с SLA, кэшированием, мониторингом и ограничением запросов. Не использовать публичные демонстрационные endpoints как инфраструктуру реального такси.

GPS: Android permissions включены в manifest. Для iOS перенести ключ из `ios/Runner/Info.plist.fragment` в настоящий `Info.plist`.

Цены не утверждены и намеренно не подставляются. Карточная оплата, SMS, backend, driver app, dispatch и административная панель ещё не реализованы.

## Сборка APK с Android-телефона
Смотрите `README_PHONE_BUILD.md`: проект содержит GitHub Actions workflow для облачной сборки APK без собственного компьютера.
