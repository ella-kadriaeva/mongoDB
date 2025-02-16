// у студента с ид 10 удалить курс Engineering
db.students.updateOne(
  { _id: 10 }, 
  { $pull: { "courses": { "title": "Engineering" } } }
);

//у студента с ид  6 , удалить первую запись о посещаемости
db.students.updateOne(
  { _id: 6 }, 
  { $pop: { attendance: -1 } }
);

// посчитать количество студентов изучающих History

db.students.aggregate({$match: {"courses.title":"History"}},
                      {$group:{_id:null, count_st:{$count:{}}}})

{
  _id: null,
  count_st: 1
}