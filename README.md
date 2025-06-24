# 20250627-hands-on
Retoolハンズオン

## (1) サンプルデータ投入用SQL
```
-- Retool DB用
-- 書籍
create table books (
 book_id TEXT not null
 , title TEXT not null
 , image_url TEXT not null
 , is_popular BOOLEAN default false not null
 , create_date_time TIMESTAMP default CURRENT_TIMESTAMP not null
 , update_date_time TIMESTAMP default CURRENT_TIMESTAMP not null
 , constraint books_PKC primary key (book_id)
);

-- 書籍
insert into public.books(book_id,title,image_url,is_popular) values 
  ('10c25422-1bcb-4774-bc79-dfc18e9cfb48','React開発現場の教科書','react.jpg',True)
 , ('138e545e-60a6-4aa7-9f27-de99a5139744','GCPの教科書Ⅲ','gcp.jpg',False)
 , ('3860fd81-486a-46e4-a090-2844aadc716f','ソフトウェアテストの教科書','test.jpg',False)
 , ('7a641787-994a-4a26-81af-e4ebb23a040a','Vue.js入門','vue.jpg',False)
 , ('7c9cba4f-857b-4e95-9fe7-433bbdc85654','絵と図でわかる データサイエンス','data.jpg',False)
 , ('a4bae49f-7e24-440c-a666-a9c7a7e8ce92','エンジニアリング組織論への招待','engineering.jpg',True)
 , ('ab49c594-4aac-490d-9b4c-3a1410648975','試して理解 Linuxのしくみ','linux.jpg',False)
 , ('c5bde476-173b-4c3f-bd5e-8f14abc37a40','OKR シリコンバレー式で大胆な目標を達成する方法','okr.jpg',False)
 , ('ec9f33f9-8d2f-45a4-9aa0-376e2b96a381','システム障害対応の教科書','failure.jpg',False)
 , ('f5607577-7976-4293-a2e1-d842e8dcac7e','ゼロから作る Deep Learning','deep.jpg',True);
```

## (2) 一覧表示用SQL
```
select * from books;
```

## (3) 絞り込み機能追加SQL
```
select * from books
where title like {{'%' + textTitle.value + '%'}};
```

## (4) 更新用SQL
```
update books
set title = {{ editTitle.value }}
  , image_url = {{ editImageUrl.value }}
  , is_popular = {{ editPopular.value }}
where book_id = {{ table1.selectedRow.book_id }};
```

## (5) 新規登録用SQL
```
insert into books (book_id, title, image_url) values
   ({{ uuid.v4() }}, {{ inputTitle.value }}, {{ inputImageUrl.value }});
```

