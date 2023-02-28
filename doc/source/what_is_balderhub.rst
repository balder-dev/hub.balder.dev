What Is A BalderHub Package
***************************

BalderHub packages are normal python packages, that can easily be included into your specific project. This allows
you to reuse scenario and feature implementation from people all around the world. You only need to provide your custom
implementation that really depends on your device, but not the general test logic.


The main idea of BalderHub packages is that you can access a wide range of different tests where a lot of clever minds
has already think about. You simply need to import their scenarios, add the specific setup-device feature code for your
device and go for it. Different mock functions, helper devices or
complete testable implementations of remote devices (for example a dhcp server for dhcp-client tests) are often already
provided in these BalderHub project. This helps you and your team to develop test a lot faster.
