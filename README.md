<div align="center">

<br/>

# Enad Abulawi

**Flutter & Dart Developer** · Palestine 🇵🇸

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white&labelColor=ffffff)](https://linkedin.com/in/enadabulawi1)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=flat&logo=instagram&logoColor=white&labelColor=ffffff)](https://instagram.com/enad.dev)
[![GitHub](https://img.shields.io/badge/GitHub-111111?style=flat&logo=github&logoColor=white&labelColor=ffffff)](https://github.com/enadabulawi)
[![Profile Views](https://komarev.com/ghpvc/?username=enadabulawi&style=flat&color=0175C2)](https://github.com/enadabulawi)

</div>

---

## About

```dart
class EnadAbulawi {
  final String name = "Enad Abulawi";
  final String title = "Flutter & Dart Developer";
  final String location = "Palestine 🇵🇸";
  final int yearsOfExperience = 3;
  
  final List<String> expertise = [
    "Mobile App Development",
    "Flutter Framework",
    "Dart Programming",
    "Firebase Backend",
    "REST API Integration",
    "UI/UX Implementation",
    "State Management",
    "Package Publishing",
  ];
  
  final String funFact = "You don't have to work in tech to use coding 💡";
  
  void askMeAbout(String topic) {
    debugPrint("I can help with: $topic");
  }
}
```

---

## Skills

### 📱 Mobile Development
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat&logo=dart&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=flat&logo=android&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-000000?style=flat&logo=apple&logoColor=white)

### 🔧 Backend & Services
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat&logo=firebase&logoColor=black)
![REST APIs](https://img.shields.io/badge/REST_APIs-039BE5?style=flat&logo=postman&logoColor=white)
![Cloud Firestore](https://img.shields.io/badge/Firestore-FFA500?style=flat&logo=firebase&logoColor=white)
![Authentication](https://img.shields.io/badge/Firebase_Auth-FFCA28?style=flat&logo=firebase&logoColor=black)

### 🛠️ Tools & DevOps
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat&logo=postman&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-007ACC?style=flat&logo=visual-studio-code&logoColor=white)

### 🎨 Design Tools
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat&logo=figma&logoColor=white)
![Photoshop](https://img.shields.io/badge/Photoshop-31A8FF?style=flat&logo=adobe-photoshop&logoColor=white)
![Illustrator](https://img.shields.io/badge/Illustrator-FF9A00?style=flat&logo=adobe-illustrator&logoColor=white)

---

## Code Examples

### Custom Widget Implementation
```dart
class IslamicAppBar extends StatelessWidget {
  final String title;
  final VoidCallback onBackPressed;
  
  const IslamicAppBar({
    required this.title,
    required this.onBackPressed,
    Key? key,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.symmetric(horizontal: 16, vertical: 12),
      decoration: BoxDecoration(
        color: Color(0xFF0175C2),
        borderRadius: BorderRadius.only(
          bottomLeft: Radius.circular(16),
          bottomRight: Radius.circular(16),
        ),
      ),
      child: SafeArea(
        child: Row(
          children: [
            IconButton(
              icon: Icon(Icons.arrow_back, color: Colors.white),
              onPressed: onBackPressed,
            ),
            Expanded(
              child: Text(
                title,
                style: TextStyle(
                  fontSize: 18,
                  fontWeight: FontWeight.bold,
                  color: Colors.white,
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

### Firebase Integration Pattern
```dart
class QuranRepository {
  final FirebaseFirestore _firestore = FirebaseFirestore.instance;
  
  Future<List<Surah>> getSurahs() async {
    try {
      final snapshot = await _firestore
          .collection('quran')
          .orderBy('number')
          .get();
      
      return snapshot.docs
          .map((doc) => Surah.fromMap(doc.data()))
          .toList();
    } on FirebaseException catch (e) {
      print('Firebase Error: ${e.message}');
      rethrow;
    }
  }
  
  Future<void> saveUserPreference(String userId, String key, dynamic value) async {
    await _firestore
        .collection('users')
        .doc(userId)
        .set({
          'preferences': {key: value}
        }, SetOptions(merge: true));
  }
}
```

### State Management with Provider
```dart
class AzkarProvider extends ChangeNotifier {
  List<Azkar> _azkarList = [];
  bool _isLoading = false;
  
  List<Azkar> get azkarList => _azkarList;
  bool get isLoading => _isLoading;
  
  Future<void> fetchAzkar() async {
    _isLoading = true;
    notifyListeners();
    
    try {
      final repository = QuranRepository();
      _azkarList = await repository.getAzkar();
    } catch (e) {
      print('Error fetching Azkar: $e');
    } finally {
      _isLoading = false;
      notifyListeners();
    }
  }
  
  void addFavoriteAzkar(Azkar azkar) {
    azkar.isFavorite = !azkar.isFavorite;
    notifyListeners();
  }
}
```

### API Integration with Dio
```dart
class ApiClient {
  final Dio _dio = Dio(
    BaseOptions(
      baseUrl: 'https://api.example.com',
      connectTimeout: Duration(seconds: 10),
      receiveTimeout: Duration(seconds: 10),
    ),
  );
  
  Future<List<Prayer>> getPrayerTimes(String city) async {
    try {
      final response = await _dio.get('/prayer-times', 
        queryParameters: {'city': city});
      
      return (response.data as List)
          .map((prayer) => Prayer.fromJson(prayer))
          .toList();
    } on DioException catch (e) {
      print('API Error: ${e.message}');
      rethrow;
    }
  }
}
```

---

## Projects

### 📖 Noor App
**Islamic companion application**
```
Platform: Android & iOS
Status: Live on Google Play Store
Downloads: 1000+
Technologies: Flutter, Firebase, Provider, Dio
Features: Quran reading, Daily Azkar, Prayer times
```
[Download](https://play.google.com/store/apps/details?id=com.Enad.Noor&hl=ar)

### 🕌 Mushaf Noor
**Beautiful Quran reading experience**
```
Platform: Android & iOS  
Status: Active Development
Technologies: Flutter, Cloud Firestore, Hive
Features: Smooth reading, Bookmarks, Search, Tajweed
```
[Download](https://play.google.com/store/apps/details?id=com.Noor.MushafNoor&pli=1)

### 📦 Snackly Package
**Elegant notification widgets for Flutter**
```dart
// Usage example
Snackly.show(
  context: context,
  message: 'Operation successful',
  type: SnacklyType.success,
  duration: Duration(seconds: 3),
  position: SnacklyPosition.bottom,
);
```
[View on pub.dev](https://pub.dev/packages/snackly)

---

## Development Approach

### Architecture Pattern
```
lib/
├── models/              # Data models
├── services/            # API & Firebase services
├── repositories/        # Data layer
├── providers/           # State management
├── screens/            # UI screens
├── widgets/            # Custom widgets
└── utils/              # Utilities & helpers
```

### Best Practices
✅ Clean Architecture principles  
✅ SOLID design principles  
✅ Provider for state management  
✅ Proper error handling  
✅ Firebase best practices  
✅ Responsive UI design  
✅ Code documentation  
✅ Git version control  

---

## GitHub Statistics

<div align="center">

[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=enadabulawi&show_icons=true&theme=default&hide_border=true&title_color=000000&icon_color=0175C2&text_color=555555&bg_color=ffffff&include_all_commits=true)](https://github.com/enadabulawi)

[![Top Languages](https://github-readme-stats.vercel.app/api/top-langs?username=enadabulawi&layout=compact&theme=default&hide_border=true&title_color=000000&text_color=555555&bg_color=ffffff)](https://github.com/enadabulawi)

</div>

<div align="center">

[![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=enadabulawi&theme=default&hide_border=true&ring=0175C2&fire=0175C2&currStreakLabel=0175C2)](https://github.com/enadabulawi)

</div>

---

## Experience Highlights

**3+ Years of Mobile Development**
- Built and published 2 production apps on Google Play Store
- Published open-source Flutter package (snackly)
- Integrated Firebase services (Firestore, Auth, Cloud Functions)
- Implemented modern state management solutions
- Created responsive UI for multiple device types
- Optimized app performance and user experience

---

<div align="center">

<br/>

**من فلسطين، نبني للعالم** 🇵🇸

<sub>Let's build something amazing together — [Connect with me](https://linkedin.com/in/enadabulawi1)</sub>

</div>
