# Proiect gestiunea produselor intr-un depozit

# 1. Database(Apache Derby DB)
  - prima data am creat baza de date "depozitDB", care contine tabele product, si am adaugat niste inregistrari:
  
    ![image](https://user-images.githubusercontent.com/44323117/146452080-3bf15a52-1016-4096-bd28-bf0c56aa97bb.png)

# 2. Backend 
  - am facut o aplicatie de tip Maven, care avea un schelet cu 3 module db, rest, si ear
  - modulul db contine partea de persistenta: JPA-ul/clasa Entity(clasa Product) si EJB-ul(clasa ProductEjb)
    ## a. JPA(Java Persistence API)
  - faciliteaza transferul datelor catre/dinspre baza de date
  - implica un persistence.xml
  - obiectele ‘Entity’ sunt instante in memorie a claselor entitate si care contin datele efective din baza de date
  - am creat clasa Product care este Entitatea(adica un obiect al clasei contine datele efective ale bazei de date)
  - Product e legata la tabela din baza de date prin: @Table(name = "PRODUCT")
  - Product contine cate un camp privat(cu setter si getter) pentru fiecare coloana din baza de date, folosind @Column
  - am adaugat Persistence Unit, care din cate am inteles, este folosit de clasa ejb pentru a face conexiunea cu baza de date
  - la prima versiune a proiectului am adaugat si o clasa de test (Proiect_Lab3Test) care folosea si Persistence Unit-ul
  - cu aceasta clasa de test, am testat daca merge bine clasa Product, afisand datele din baza de date:

  ![image](https://user-images.githubusercontent.com/44323117/146451393-b1ae2b39-1853-48aa-be95-14aa0dc99d6a.png)

  - dupa acestea am definit un bazin de conexiuni (Connection Pool) si o resursa jdbc (JDBC Resource) pentru baza de date pe care o am
  
    ## b. EJB(enterprise java bean)
  - clasa EJB se foloseste de EtityManager pentru a intermedia obtinerea de instante de tip Entity
  - asigura tranzactionabilitatea; sa facem o tranzactie(commit) pe baza de date doar la finalul metodei
  - injection, sistemul face automat instantierile
  - am creat clasa ProductEjb cu care fac anumite operatii pe baza de date: **getList**, **filter**, **findById**, **createProduct**, **updateProduct**, **deleteProduct**
  - aceasta clasa are anotarea @Stateless care determina ca o clasa java sa fie considerata EJB si in consecinta sa beneficieze de tranzactionabilitate
  
    ## c. REST
  - folosit pentru servicii de tip REST
  - serviciile EJB le expun cu adnotarile aferente aub forma de REST, celor care vor sa le consume
  - inregistreaza pe server(glassfish) niste URL-uri, iar daca cineva le apeleaza, se raspunde cu ceva
  - se foloseste de EJB pentru a comunica cu baza de date
  - am definit "aplicatia" LabRestApplication
  - am creat clasa RestProduct, in care am niste metode(de ex. **getList, updateProduct, filter**) care se folosesc de metodele din clasa ProductEjb pentru a expune metodele celor care vor sa le consume 

# 3. Frontend 
  - preia datele de la REST, si le afiseaza
  - gestioneaza interactiunile cu utilizatorul
  - clasa ProductDto reprezinta materializarea datelor obtinute de la serviciul web obiecte java



