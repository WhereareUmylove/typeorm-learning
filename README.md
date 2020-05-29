# typeorm-learning
    createQueryBuilder("user")
        .where("user.registered = :registered", { registered: true })
        .andWhere(new Brackets(qb => {
            qb.where("user.firstName = :firstName", { firstName: "Timber" })
              .orWhere("user.lastName = :lastName", { lastName: "Saw" })
        }))
    相等于
    SELECT ... FROM users user WHERE user.registered = true AND (user.firstName = 'Timber' OR user.lastName = 'Saw')

</br>
一对一连表查询：

        let qb = await getConnection()
          .createQueryBuilder(Player,'player')
          .leftJoinAndMapOne('player.currency',PlayerCurrency,"player_currency", 'player.id=player_currency.player_id')
          .orderBy('player.id', 'DESC');
          
一对多连表查询：

            leftJoinAndMapMany
