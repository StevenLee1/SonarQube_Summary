Now we have two SonarQube environments. Each time we want to write analysis report to different SoanrQube. Fortunately Maven use Profile which provides a flexible way to do this configuration.

We use settings.xml to do global configuration, below is the configuration:

```
<pluginGroups>
	<pluginGroup>org.sonarsource.scanner.maven</pluginGroup>
</pluginGroups>

<profiles>
	<profile>
            <id>sonar-site1</id>
            <activation>
                <activeByDefault>false</activeByDefault>
            </activation>
            <properties>
                <sonar.host.url>
                  http://x.x.x.x
                </sonar.host.url>
				<sonar.login>
					xxx
				</sonar.login>
				<sonar.password>
					xxx
				</sonar.password>
            </properties>
    </profile>
	
	<profile>
            <id>sonar-site2</id>
            <activation>
                <activeByDefault>false</activeByDefault>
            </activation>
            <properties>
                <sonar.host.url>
                  http://x.x.x.x
                </sonar.host.url>
				<sonar.login>
					xxx
				</sonar.login>
				<sonar.password>
					xxx
				</sonar.password>
            </properties>
    </profile>
<profiles>
```

then use command line to generate report:

mvn verify sonar:sonar -Psonar-site1   or

mvn verity sonar:sonar -Psonar-site2