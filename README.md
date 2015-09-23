# How to (locally) render a simulation
## Clone that repository and install jekyll
```sh
git clone https://github.com/vhuber/present_simu
brew install ruby
gem install jekyll
```
## In your code
  ```cpp
if ( Environment::worldComm().isMasterRank()  )
{
  std::ostringstream stringStream;
  stringStream << 1900+ltm->tm_year<<"_"<<ltm->tm_mon<<"_"<<ltm->tm_mday<<"-"<<ltm->tm_hour<<ltm->tm_min<<ltm->tm_sec<<"_"<<"myAwesomeTitle"<<".md";
  std::ofstream outputFile( stringStream.str() );
  if( outputFile )
  {
    outputFile 
      << "---\n"
      << "title: \""<< soption("title") << "\"\n"
      << "date: " << stringStream.str() << "\n"
      << "categories: simu\n"
      << "--- \n\n";
    outputFile << "#Physique" << std::endl;
    model.saveMD(outputFile); 

    outputFile << "##Mesh" << std::endl;
    M_mesh->saveMD(outputFile); 

    outputFile << "##Timers" << std::endl;
    Environment::saveTimersMD(outputFile);
  }
  else
  {
    std::cerr << "Failure opening " << stringStream.str() << '\n';
  }
}
```
You can write directly in the `outputFile` to generate specific markdown.

## Once executed
```sh
cd present_simu/_simu
ln -s /tmp/user/feelpp/<...>/*md .
cd ..
jekyll serve
```

and open in a browser [http://localhost:4000](http://localhost:4000)

You can also use `jekyll build` to generate the website and then copy it somewhere (in `_public_html` ?)
