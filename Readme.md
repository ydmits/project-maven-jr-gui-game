Задание: Нужно сделать исполняемый JAR-файл с игрой на JavaFX через графический движок от JavaRush.

Для этого нужно:

    1 Сделать fork из репозитория https://github.com/vasylmalik/project-maven.git
    2 Скачать свою версию проекта к себе на компьютер. Дальше будем работать с файлом pom.xml.
    3 Добавить зависимости:
        org.apache.commons: commons-lang3: 3.12.0
        org.openjfx: javafx-controls: 18.0.1
        com.javarush: desktop-game-engine:1.0 (об этой зависимости будет отдельное задание)
        org.junit.jupiter: junit-jupiter-engine: 5.8.2 (с scope test)
    4 Добавить плагины для:
        установки зависимости com.javarush: desktop-game-engine:1.0 из библиотеки lib в локальный репозиторий (google в помощь);
        плагин maven-compiler-plugin оставить без изменений;
        плагин, который соберет все зависимости (с scope compile) и сложит в какую-то директорию при сборке;
        плагин maven-jar-plugin, который сделает jar файл, содержащий код игры и зависимости. В этом плагине нужно сконфигурировать файл MANIFEST.MF, чтоб он содержал секции: Class-Path, Main-Class и Rsrc-Main-Class
        В Class-Path должны быть прописаны все наши JAR-зависимости.
        В Main-Class должен быть прописан класс org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader, который умеет использовать classpath из JAR-файлов, а также умеет стартовать приложение на JavaFX.
        В Rsrc-Main-Class должен быть прописан стартовый класс игры (com.javarush.games.racer.RacerGame).
    5 В плагине maven-surefire-plugin сделать конфигурацию, чтоб тест StrangeTest не запускался при сборке. Остальные тесты должны выполняться.
    6 Добавить секцию “resources”, в которой сказать, что собранные JAR-зависимости это ресурс, чтоб плагин maven-jar-plugin сложил их внутрь JAR-файла в папку lib/
    7 Залить изменения в свой GitHub-репозиторий, отправить ссылку на него преподавателю.