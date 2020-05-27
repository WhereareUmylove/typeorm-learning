# typeorm-learning
createQueryBuilder("user")
    .where("user.registered = :registered", { registered: true })
    .andWhere(new Brackets(qb => {
        qb.where("user.firstName = :firstName", { firstName: "Timber" })
          .orWhere("user.lastName = :lastName", { lastName: "Saw" })
    }))
    
    SELECT ... FROM users user WHERE user.registered = true AND (user.firstName = 'Timber' OR user.lastName = 'Saw')
