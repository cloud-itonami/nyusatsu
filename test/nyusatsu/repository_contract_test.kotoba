(ns nyusatsu.repository-contract-test
  (:require [clojure.edn :as edn]
            [clojure.test :refer [deftest is]]))

(deftest standalone-edn-metadata
  (doseq [path ["manifest.edn" "identity.edn" "dependencies.edn"
                "repository-contracts.edn" "migration.edn" "schema.edn"]]
    (is (some? (edn/read-string (slurp path))) path)))

(deftest wire-boundary
  (let [contract (edn/read-string (slurp "repository-contracts.edn"))]
    (is (= :edn (:canonical-data contract)))
    (is (= "wire" (get-in contract [:external-formats :root])))))
