The language I’ve chosen for my analysis is C#.

For linting as part of a CI setup, I would use ReSharper command line tools by JetBrains. It consists of
two tools, InspectCode and CleanupCode, that can be integrated into a CI setup. The first tool,
InspectCode executes hundreds of ReSharper code inspections. The latter, CleanupCode will
instantly eliminate code style violations and makes sure there is a uniform code base.

For testing, I would pick XUnit. It is an open-source automation unit testing tool for the .NET
platform. It also integrates quite well into ReSharper. It is also far more straight forward to use when
compared to other unit testing frameworks – e.g., no need to explicitly set up and tear down tests, it
is a lot more extensible, single object instance per method ensures each test is run independently.
Finally, it also supports the generation of a code coverage file that can later be used by code
coverage analysis tools to generate details reports.

Finally for building, I would simple use the donet build command that is included in the .NET CLI. The
IDEs used for development most certainly use dotnet build under cover to build the solution, so why
not use the same tool during the build step of our CI.

There are many alternatives to GitHub Actions and Jenkins, such as Azure Pipelines and JetBrains
TeamCity. They both can be hosted on either on-premises or in the cloud.

The question of whether the setup is better off self-hosted or in a cloud-based environment depends
on several factors. The major one would be cost, as cost in a cloud-based environments depends on
how often you use the cloud resources. Another factor that is most often overlooked is if there are
DevOps personnel within the team, if the CI was to be self-hosted. The developers most often won’t
have the time to worry about making sure the hardware and OS of the self-hosted server is up-to-
date properly, it would be better if they spend most of their time on developing the product itself.
Finally, what are the organization’s cyber security policies? Some organizations may be strict in that
they would not allow internal IP to be sent “externally” to cloud-based environments. Basically, all IP
needs to be retained within the corporate boundaries.
