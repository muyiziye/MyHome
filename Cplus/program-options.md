### c++ 使用boost库处理输入参数

---

- 可以使用的代码

<pre>

/*************************************************************************
*
* check_ipmi.cpp
*
* CREATE ON:  2017_11_16
* BY       :  liuyang70@lenovo.com
*
*************************************************************************/
#include <iostream>
#include \<sstream>
#include \<string>
#include \<boost/program_options.hpp>

using namespace std;
namespace bpo = boost::program_options;

int add_options_kcs(bpo::options_description &opts);
int add_options_lan(bpo::options_description &opts);
int add_options_general(bpo::options_description &opts);

int main(int argc, char **argv) 
{
	bpo::options_description opts("all options");
	bpo::options_description opts_lan("lan options");
	bpo::options_description opts_kcs("kcs options");
	bpo::options_description opts_general("general options");

 	add_options_kcs(opts_kcs);
	add_options_lan(opts_lan);
	add_options_general(opts_general);

	opts.add(opts_kcs).add(opts_lan).add(opts_general);
	bpo::variables_map vm;
	try {
		bpo::store(bpo::parse_command_line(argc, argv, opts), vm);
	}catch(...){
		cout << opts << endl;
	}
	
	if(vm.count("help")) {
		cout << opts << endl;
		return 0;
	}

	if(vm.count("kcs")) {
		if(vm.count("node")) {
			cout << "node: " << vm["node"].as<int>() << endl;
		}
		cout<<"just for test " <<endl;
		return 0;
	}else if(vm.count("lan")) {
		if(vm.count("hostip")) {
			cout << "ip: " <<  vm["hostip"].as<string>() << endl;
		}
		if(vm.count("userid")) {
			cout << "userid: " << vm["userid"].as<string>() << endl;
		}
		if(vm.count("password")) {
			cout << "password: " << vm["password"].as<string>() << endl;
		}
		if(vm.count("port")) {
			cout << "port: " << vm["port"].as<string>() << endl;
		}
		cout<<"just for test 2 " <<endl;
		return 0;
	}

	return 0;
}

int add_options_lan(bpo::options_description &opts)
{
	opts.add_options()
		("lan,L", "This tool will connect the machine via LAN")
		("hostip,H", bpo::value<string>(), "Set the hostaddress for the machine which you want to get information from")
		("userid,U", bpo::value<string>(), "Set the userid for the machine which you want to get information from")
		("password,P", bpo::value<string>(), "Set the password for the machine which you want to get information from")
		("port,p", bpo::value<string>(), "Set the port for the machine which you want to get information from");
	return 0;
}

int add_options_kcs(bpo::options_description &opts)
{
	opts.add_options()
		("kcs,K", "This tool will connect the machine via KCS")
		("node,n", bpo::value<int>(), "Set the node for the machine which you want to get information from");
	return 0;
}

int add_options_general(bpo::options_description &opts)
{
	opts.add_options()
		("help,h", "Get the help message for this tool");
	return 0;
}



</pre>