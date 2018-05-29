Tasks:
1) Increase unit test coverage to reach 70%, achieving more than 70% will only consume your valuable time without extra score.

Added/Updated test case classes:

ArticleServiceImplTest.java
CommentServiceImplTest.java
CommentControllerTest.java
ArticleServiceImplTest.java


2) Find bugs and fix them, hint: we provided Cross-Blogs application in a good structure, so no need to spend your valuable time on structure modifications,  just focus on fixing bugs.

Updated Article.java to use length attribute instead of size for validation below:
- Articles have a 120 character limit for their title, and a 32k limit for their body.
length attribute exception handling will automatically be done by GlobalExceptionHandler.java
-Added validation at service layer also so if any other controller in future uses the service ArticleService, then validation of title and content should happen. So, at service layer, it will explicitly through custom exception ArticleException (which is new custom defined exception class.)
-Updated Comment.java to use length attribute instead of size for validation.

3) Articles search title endpoint is very slow, please optimize it.
findTop10ByTitleContainingIgnoreCaseOrContentContainingIgnoreCase method in ArticleRepository gave me fast results so I didn't change it.
There is a work around to have a @Query on the method for adding query rather than using in-built method as below:
@Query("SELECT a FROM Article a WHERE  lower(a.title) LIKE concat('%', lower(:title), '%') or lower(a.content) LIKE concat('%', lower(:content), '%')")
and then adding PageResult




