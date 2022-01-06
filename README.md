#  Домашнее задание к занятию "09.05 Teamcity"

Подготовка к выполнению

##  1. В Ya.Cloud создайте новый инстанс (4CPU4RAM) на основе образа jetbrains/teamcity-server

done

##  2. Дождитесь запуска teamcity, выполните первоначальную настройку

3.Создайте ещё один инстанс(2CPU4RAM) на основе образа jetbrains/teamcity-agent. Пропишите к нему 
переменную окружения SERVER_URL: "http://<teamcity_url>:8111"

done

## 4. Авторизуйте агент

done

##  5. Сделайте fork репозитория

https://github.com/olegrovenskiy/example-teamcity

done



#  Основная часть

##  1. Создайте новый проект в teamcity на основе fork

JAVA Project

done

##  2. Сделайте autodetect конфигурации

done

##  3. Сохраните необходимые шаги, запустите первую сборку master'a

done

https://c2n.me/4ewXwY6

##  4. Поменяйте условия сборки: если сборка по ветке master, 
то должен происходит mvn clean deploy, иначе mvn clean test

done

https://c2n.me/4ex2bfj

##  5. Для deploy будет необходимо загрузить settings.xml в набор конфигураций maven у teamcity, 
предварительно записав туда креды для подключения к nexus

	<id>nexus</id>

	<username>admin</username>

	<password>admin123</password>

	</server>

##  6. В pom.xml необходимо поменять ссылки на репозиторий и nexus

		<id>nexus</id>
		<url>http://51.250.15.162:8081/repository/maven-releases</url>
		

##  7. Запустите сборку по master, убедитесь что всё прошло успешно, артефакт появился в nexus

done

https://c2n.me/4ewZiMS

##  8. Мигрируйте build configuration в репозиторий

done

##  9. Создайте отдельную ветку feature/add_reply в репозитории

	vagrant@vagrant:~/HW-9.5/example-teamcity$ git status
	On branch feature/add_reply
	nothing to commit, working tree clean
	vagrant@vagrant:~/HW-9.5/example-teamcity$

##  10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово hunter

	package plaindoll;
	
	public class Welcomer{
		public String sayWelcome() {
			return "Welcome home, good hunter. What is it your desire?";
		}
		public String sayFarewell() {
			return "Farewell, good hunter. May you find your worth in waking world.";
		}
	
	        public String sayNew() {
			return "New, good hunter. Good news, you are the winer.";
		}
	
	}
	

##  11. Дополните тест для нового метода на поиск слова hunter в новой реплике

	@Test
		public void welcomerSaysNew() {
			assertThat(welcomer.sayNew(), containsString("hunter"));


##  12. Сделайте push всех изменений в новую ветку в репозиторий

done

##  13. Убедитесь что сборка самостоятельно запустилась, тесты прошли успешно

done

https://c2n.me/4ex23w0

##  14. Внесите изменения из произвольной ветки feature/add_reply в master через Merge

	vagrant@vagrant:~/HW-9.5/example-teamcity$ git merge feature/add_reply
	Updating df5ea86..ae0a561
	Fast-forward
	 src/main/java/plaindoll/Welcomer.java     | 3 +++
	 src/test/java/plaindoll/WelcomerTest.java | 7 ++++++-
	 2 files changed, 9 insertions(+), 1 deletion(-)
	vagrant@vagrant:~/HW-9.5/example-teamcity$

##  15. Убедитесь, что нет собранного артефакта в сборке по ветке master

done

##  16. Настройте конфигурацию так, чтобы она собирала .jar в артефакты сборки

done

##  17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны

done

##  18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity

done

https://c2n.me/4ex3ymi
