
House Prices - Advanced Regression Techniques:

ჩვენი მიზანია, აიოვას შტატში კერძო სახლების 79 პარამეტრის გამოყენებით დავატრენინგოთ მოდელი, 
რომელიც აკურატულ ვარაუდს მოგვცემს სახლის მოსალოდნელ ფასზე

მიდგომა: 

ჩემი მთავარი მიდგომა Prediction-ის ოპტიმიზაციისთვის იყო არა მხოლოდ სხვადასხვა ტექნიკებისა და ფილტრების გამოყენება,
არამედ პარამეტრებზე ანალიზი და ისეთი პარამეტრების თავიდან მოშორება, რომელიც არავითარ გავლენას არ ახდენდა ფასზე

სტრუქტურა:

model_experiment.ipynb - მთავარი ფაილი, სადაც წერია ყველაზე ოპტიმალური მოდელის კოდი

model_inference.ipynb - ფაილი, სადაც ხდება test set -ზე პროგნოზი.

mlData - ფოლდერი, სადაც ინახება csv ფაილები.
 

Feature Engineering:
კატეგორიული ცვლადების რიცხვითში გარდასაქმნელად გამოვიყენე სხვადასხვა მიდგომები, როგორიცაა getDummies და OneHotEncoder

null მნიშვნელობების შესავსებად გამოვიყენე standardScaler, MinMaxScaler და RobustScaller.

თუმცა, null მნიშვნელობების მქონე პარამეტრებზე დაკვირვებისას, ადვილი შესამჩნევი იყო რომ მათი უმრავლესობა (1-2) გამონაკლისის გარდა:
1) საერთოდ არ ახდენდა SalePrice პარამეტრზე გავლენას (რასაც გრაფების დაგენერირებით ვაკვირდებოდი)
2) ახდენდა გავლენას SalePrice-ზე, მაგრამ მისი როლს უკვე მოიცავდა სხვა პარამეტრი (მაგალითად, GarageQual პარამეტრი მთლიანად მოიცავს ყველა სხვა Garage პარამეტრს)

არ შევხებივარ ისეთ პარამეტრებს, რომლებიც არ შეიცავდნენ null-ებს, მაგრამ ზოგი ამ პარამეტრის მოშორებითაც შესაძლებელია შედეგის კიდევ უფრო გაუმჯობესება

ასევე ძალიან კარგი შედეგი მოგვცა მონაცემების დატრენინგებამ ფასის ლოგარითმზე. 

Training:

დასატრენინგებლად გამოვიყენე GridSearch, რომელიც ბევრ სხვადასხვა ტრენინგის მიდგომიდან მაჩვენებდა საუკეთესო ტექნიკებს, 
საინტერესოა, რომ როცა მოდელს ვატრენინგებდი ფასის ლოგარითმზე, დატრენინგების ყველაზე ეფექტური ტექნიკა იყო Ridge, 
ხოლო უბრალოდ ფასზე დატრენინგებისას Random Forest გვაძლევდა საუკეთესო შედეგს. 


ექსპერიმენტების ლინკი:

https://dagshub.com/CarlTeapot/ML_assignment1/experiments#/
