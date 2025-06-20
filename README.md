// Gyms
Table gym {
  id        int       [pk, increment]   // unique gym identifier
  name      varchar
  address   varchar
  phone     varchar
}

// Members
Table member {
  id          int       [pk, increment]
  last_name   varchar
  first_name  varchar
  address     varchar
  birth_date  date
  gender      varchar
  gym_id      int       [ref: > gym.id]  // FK → gym
}

// Sessions
Table session {
  id          int       [pk, increment]
  sport_type  varchar
  schedule    datetime
  gym_id      int       [ref: > gym.id]  // FK → gym
}

// Coaches
Table coach {
  id          int       [pk, increment]
  last_name   varchar
  first_name  varchar
  age         int
  specialty   varchar
}

// Member–Session (M:N)
Table registration {
  member_id    int   [pk, ref: > member.id]
  session_id   int   [pk, ref: > session.id]
  registered_on date
}

// Session–Coach (M:N)
Table session_coach {
  session_id  int  [pk, ref: > session.id]
  coach_id    int  [pk, ref: > coach.id]
}